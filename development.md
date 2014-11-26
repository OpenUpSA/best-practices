# Code for SA Development Best Practices

We build a range of sites, microsites, tools and visualisations for ourselves and our clients. We recommend sticking to these technical best practices to make it it easier for us to delivery quality, and build, deploy and maintain our projects. We do our best to follow industry best practices to make it easier for other groups to build on our projects.

These aren’t rules. If you the situation calls for something different, talk to someone and make the most informed decision you can.

If you have a better practice, speak up and motivate for it.

# Guidelines

- Always do your best to ensure a good user experience
- Repeatability and consistency is important for reuse
- Prefer reuse over building from scratch
- Make data-driven decisions

# Best Practices

## Languages and Frameworks

- Use Python if at all possible. It’s mature, has rich libraries and frameworks, is widely used in the Open Data community, is performant and easy to learn.
- Use Flask for small sites and APIs. It’s mature, small, simple to use and understand, and has a reasonable collection of plugins.
- Use pip to manage dependencies.
- Use virtualenv to sandbox your projects.
- Use PostgreSQL if you need a big database (ie. not Mysql), sqlite if you need a small one.
- Use PostGIS for geo data.
- Use Bootstrap.
- Use jQuery.

### Recommended Frameworks

- Use leaflet.js for maps.
- Use D3 for datavis.

## Source code

- Store code on Github under the Code4SA account - https://github.com/Code4SA/
- Always include a README.md and a LICENSE. MIT and Apache are recommended, see http://choosealicense.com/
- Deploy from the master branch
- Branch early, commit often
- Remember: our community judges us on the quality of our code!

## Sensitive Data (Credentials, etc.)

- Never commit sensitive credentials or other information into the repo. If it happens accidentally, remove them from the source and change them.
- Sensitive data should be stored in a Google Sheets document in the project’s Google Drive folder and shared with your team mates, to improve your bus factor.
- Sensitive data should be injected into the application through environment variables or some other mechanism that doesn’t involve checking it into source control.

Sensitive data includes:

- AWS credentials
- Database credentials
- Flask/Django secret keys for session cookies

This data is NOT sensitive:

- Google Analytics ids (it gets sent to the client in any case)
- New Relic license key 

## Build, Test, Deploy
 
**Goal**: simple, consistent, well documented

- Document how to setup a local development environment in your README.md.
- If your code needs to be built, it should be possible with one command.
- Document how to deploy into production in your README.md. If it’s really hard/long/complex to do this, then you’re probably doing deployment the wrong way.
- Running tests should be one command (eg. nosetests)
- Production deployment should be one command (eg. git push, fab deploy). This will be critical when the server dies (and it will!)
- Version your dependencies. Use pip freeze to save dependencies into a single requirements.txt file.
- Don’t worry about separate production and development requirements files, just use one.

## Platforms

Prefer platforms that encourage simple, consistent deployments and make collaboration easy.

- Apps that don't require server logic should be hosted using [GitHub Pages](https://pages.github.com/).
- Apps that require simple server logic such as a database should be deployed to [Heroku](http://heroku.com).
- Only deploy to our own infrastructure if it's truly required.

## Databases

- Always keep customer data backed up

## Monitoring

- Use New Relic wherever possible (TODO: instructions for integrating into Flask)

## Branding

- Include our logo, linking to www.code4sa.org
- Include a link to https://twitter.com/Code4SA - make it easy for users to contact us
- Include a link to the Github repo for the project.
- If the data is available on data.code4sa.org, link to it.

## Development Process

- Perfect is the enemy of done.
- Time-box experiments. Commit to a go/no-go deadline after a day or two of work. At that point, honestly discuss with someone else whether you should continue or learn and discard.
- Try to have at least 2 developers involved on each project, at least with code reviews or design discussions. If you can’t convince one person, then your idea might suck.