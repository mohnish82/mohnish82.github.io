---
layout: post
title: LFTP - the sophisticated ftp/http client
---

The author of the famous LFTP[http://lftp.yar.ru/] tool, defines it as a sophisticated ftp/http client. After using it for a couple of months, I can now attest to that claim.
It is feature loaded and provide many niceties. Some of the features I use regularly are segmented downloads (splitting a file into parts and transferring those parts concurrently), queues, 
directory download/upload and resume.

Quick reference:

Download a directory
> mirror -c --use-pget-n=3 dir_name
 : c => resume
 : use-pget-n => segmented download with 3 chunks

Upload a directory
> mirror -R -c --use-pget-n=3 <dir_name>

Put current command in background
> Ctrl-Z

Bring backgrounded command back
> wait

Create an empty queue
> queue stop
> queue (if no queue exists)

Queue status (execute only if queue exists, otherwise it would create an empty queue)
> queue

Add current executing command to queue
> queue wait 0

Stop further queued actions (but keep current ones going)
> queue stop

Start all stopped queues
 - exit out of lftp. Upon exit it automatically starts all stopped queues

It can use the SSH Agent to connect using already added keys. On my raspberrypi, I do the following for SFTP connection using SSH Agent:
> Start SSH agent
> Add desired key to SSH agent (PS: On raspberry pi, need to execute 'eval '$(ssh-agent)')
> lftp sftp://<user>@<server>

If asks for password, but hitting ENTER key allows it to connect using the SSH agent. 
