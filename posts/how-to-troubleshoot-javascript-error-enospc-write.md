---
title: How to troubleshoot npm ERR Error ENOSPC
authorSlug: macarena-pecha
authorDisplayName: Macarena Pecha
tags: [tutorial, JavaScript, NPM, troubleshooting]
publicationDate: October 26, 2021
description: Learn how to error handle npm ERR Error ENOSPC, write
image: https://storage.googleapis.com/sourcegraph-assets/learn/headers/sourcegraph-learn-header.png
imageAlt: Sourcegraph Learn
browserTitle: npm ERR Error ENOSPC, write in JavaScript error handling
type: posts
---

If you are working in JavaScript, and receive the following output, then there is no space on the drive. 

<Highlighter
input='Error: ENOSPC.'
/>

This is likely to be a limit on the number of file watches. The system has a limit to how many files can be watched by a user. The npm package manager, or a process controlled by it, is watching too many files. 

## Reproducing the error

This error can occur with Node.js when uploading files to a web server. When beginning to upload files to the server, the Node.js process hangs and shows the error.

You can reproduce it through opening multiple NodeJS or ReactJS projects simultaneously.

## Verify the cache 

Using npm, you can verify that all the items in the cache are necessary with the following command.

<PrismSyntaxHighlighter
input='npm cache verify'
language='bash'
/>

Running this command will ensure that all items in the cache are actively relevant, it will compress the cache, and collect garbage.

As of npm@5, the cache self heals and it is not generally necessary to clear the cache. 

If you are debugging and want to start with a clean cache, you can empty your current cache into a temporary folder (to restore it later) with the `npm install --cache /tmp/empty-cache` command.

## Using a different temporary folder

**Tmp** or **temp** generally means some kind of temporary storage, which is auto-generated by a program (generally per each session).

You can configure npm to use a different temporary folder by setting that up specifically, with the following command. 

<PrismSyntaxHighlighter
input='npm config set tmp /path/to/some/other/dir'
language='bash'
/>

This will help streamline your programming environments so you are only working with the files relevant to your current project.

## Deleting the temporary folder content

Temporary files are stored by default in the folder specified by the `tmp` configuration. Temporary files are given a unique folder under this root for each run of the program, and are deleted upon successful exit.

If you are no longer using the items in your temporary directory, you can delete everything out of the `npm/tmp` folder to streamline your work. 

## Increasing the maximum number of watches a user can have

On Linux, the development server uses [inotify](https://en.wikipedia.org/wiki/Inotify) to implement hot-reloading (only refreshing files that have code changed). The inotify API allows the development server to watch files and be notified when they change.

The default inotify file watch limit varies from distribution to distribution (for example, it's `8192` on Ubuntu and Fedora). The needs of the development server often exceeds this limit.

You can run out of watches pretty quickly if you have Grunt running with other programs like Dropbox.

The recommended approach is to try increasing the file watch limit temporarily while you are working on your application. This command increases the maximum amount of watches a user can have.

Run the below command to get output of your current limit:

<PrismSyntaxHighlighter
input='sysctl fs.inotify.max_user_watches'
language='bash'
/>

Your output will be a number, such as:

<Highlighter
input='8192'
/>

To temporarily set a new limit, you can run the following command. This will temporarily reset your limit to `524288`. 

**Note**: be aware of the memory of the machine you are using to not over-extend your system.

<PrismSyntaxHighlighter
input='sysctl fs.inotify.max_user_watches=524288 && sudo sysctl -p'
language='bash'
/>

This limit will revert after a reset. At this point, you can restart your development server to check that the new limit allows you to continue working without encountering the `ENOSPC` error. 

## Learn more

Search across open source JavaScript repositories that have the `Error: ENOSPC` message to understand it more.

<SourcegraphSearch query="Error: ENOSPC" patternType="literal"/>

Check out more Sourcegraph Learn tutorials on [JavaScript](https://learn.sourcegraph.com/tags/javascript).
