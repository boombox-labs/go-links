# Trotto Go Links

[![CircleCI](https://dl.circleci.com/status-badge/img/circleci/Wp5qWwVchXp4teudjvx2zq/3F8UyJs2UMqV9cR5YLdip9/tree/master.svg?style=svg&circle-token=5eb7268ab9c1eb72a0991609d3c7292340397c25)](https://dl.circleci.com/status-badge/redirect/circleci/Wp5qWwVchXp4teudjvx2zq/3F8UyJs2UMqV9cR5YLdip9/tree/master)

[![Deploy](https://www.herokucdn.com/deploy/button.svg)](https://heroku.com/deploy?template=https://github.com/trotto/go-links)

_(See the guide [here](https://www.trot.to/docs/deploy/deploy-to-heroku) to deploy to Heroku in minutes.)_

Reliable and battle-tested continuously in production since 2017, this [go links](https://www.trot.to/go-links) solution
is used by companies all around the world daily as the core of [Trotto](https://www.trot.to).

Try out the latest build at [latest-master.trotto.dev](https://latest-master.trotto.dev) and also check out the
matching [open-source browser extension](https://github.com/trotto/browser-extension).

If you'd rather use the fully-managed instance of Trotto, visit [www.trot.to](https://www.trot.to).

---

Don't hesitate to reach out to us through help@trot.to, a GitHub issue, or live chat
at https://www.trot.to.

---

## Features

Trotto provides all the baseline functionality you'd expect from a go links solution, including the ability to
create, use, and modify go links that are shared with your organization—and with nobody else.

Trotto also includes powerful features above and beyond a basic go links implementation, including a searchable go
links directory, a [browser extension](https://github.com/trotto/browser-extension) that makes go links work instantly,
and programmatic links, which are go links containing placeholders that map onto the destination
URL (ex: `go/gh/%s` pointing to `https://github.com/my_org/%s`).

For a full list of Trotto's features, check out https://www.trot.to/how-it-works.

## Authentication

At the moment, the open-source app solely supports authentication using a Google account,
but we plan to add support for additional identity providers upon request. So if you need support
for another provider, submit a GitHub issue, and we'll help you out!

## Deploy the app

See our deployment docs:

- [Deploy to Heroku](http://www.trot.to/docs/deploy/deploy-to-heroku)
- [Deploy with Docker](http://www.trot.to/docs/deploy/deploy-with-docker)

## Local development

You can bring up a local instance of Trotto within a few minutes.

### Clone this repository

```
git clone git@github.com:trotto/go-links.git
cd go-links
```

### Create a virtualenv

Inside the `go-links/server` directory, create and enter a
Python 3.8 [virtualenv](https://docs.python.org/3/library/venv.html) and install dependencies:

```
cd go-links/server
python3.11 -m venv .virtualenv
source .virtualenv/bin/activate
pip install -r src/requirements.txt
```

You can use `pyenv` as well.

### Start the backend server

From the `server/` directory, run:

```
./run_local.sh
```

### Start the frontend development server

In a separate terminal, from the `frontend/` directory, run:

```
yarn install
yarn dev
```

Now, you can access the local instance at http://localhost:3000.

### Making changes

Most server-side and frontend changes should be picked up automatically, thanks to the Flask dev server and
[React Hot Loader](https://github.com/gaearon/react-hot-loader).

### Database migrations

- update a table model file, e.g., `server/src/modules/data/implementations/postgres/links.py`
- created a revision file, e.g., `./scripts/create_revision.sh "Add unlisted column"`
- review the generated file in `server/src/migrations/versions`
- reload the app to apply the migration

### Running tests

#### Python

All tests:

```
./run_tests/run.sh
```

Subset of tests:

```
./run_tests/run.sh modules.links.tests.handlers_tests:TestUnlistedLinks
```
