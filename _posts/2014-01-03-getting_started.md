---
layout: default
title: Getting started
modal-id: getting-started
---
Firstly we will need to initialise a Git repository for your theme on our platform and provide it with an API key so it can query Hestia and get the information it needs. You don't need to do anything here and it's a stage we will automate in the future.

Once we have done this we will create you an account on ``Gitlab`` (our internal Git platform) and you will receive an automatic email containing your login information. Before you can get to work on your theme, your will need to supply Gitlab with your ``Public SSH key``. This is so you can clone and push/pull to and from your theme's repository. For information on how to fetch or generate your SSH key, visit [this link](https://help.github.com/articles/generating-ssh-keys#platform-mac).

This link will take you to the SSH section on Homeflow where you can paste in your key: ``http://hades.homeflow.co.uk/keys``.

To clone your repository, open up a command prompt and ``cd`` to directory of your choice (but one that you won't forget and is easy to get to!) and run the following:

``git clone <link>``

Your Git clone URL will look something like: ``git@hades.homeflow.co.uk:fdesign/pantani.git``.

By this point we should have provided you with a ``staging`` link so you/your team/your customer can view the development progress of the site. Once you have added your public key and you have successfully cloned your repository, we can now start to put your theme's folder structure together.