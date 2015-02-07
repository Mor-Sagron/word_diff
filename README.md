# Word Diff

Word Diff empowers you to be a Markdown person in a Microsoft Word world by automatically converting any Word document committed to a GitHub repo to Markdown.

[![Build Status](https://travis-ci.org/benbalter/word_diff.svg?branch=master)](https://travis-ci.org/benbalter/word_diff)

## How it works

Lets say you have a file called `document.docx` and you commit it to your GitHub repo.

Word Diff will automatically make a second commit, along side your commit to add a `document.md` file, with the contents of `document.docx` converted to markdown. It'll even note that you're the commit author and copy over your commit message.

If you make changes and commit a new version of `document.docx`, Word Diff will update the `document.md` file, and if you delete `document.docx`, `document.md` gets deleted as well.

Under the hood, it uses [word-to-markdown](https://github.com/benbalter/word-to-markdown).

## When you'd use this

If you're collaborating on text with someone:

1. Using Git's native diff functionality, you can quickly verified what's changed or compare changes over time
2. You can collaborate in Markdown/GitHub while the world collaborates via email/Word

## Setup

1. Create a bot account, and [create a new personal access token](https://github.com/settings/tokens/new) with `public_repo` scope
2. Set the token as a `GITHUB_TOKEN` environmental variable
3. Add the Word Diff server as a web hook on the repository, receiving push events, stored the shared secret token as `SECRET_TOKEN`

## Running on Heroku

In order to get LibreOffice installed, you'll want to run `heroku config:add BUILDPACK_URL=https://github.com/ddollar/heroku-buildpack-multi.git`. This will instruct Heroku to read the `.buildpacks` file.

## Running locally

1. `bundle exec rackup`
2. Follow the [ngrok documentation](https://developer.github.com/webhooks/configuring/#using-ngrok) to forward requests to your computer if you don't want to set up a development server
