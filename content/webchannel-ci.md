Title: Webchannel-ci
Date: 2015-07-15 12:33
Modified: 2015-07-15 12:33
Category: Brain-Dump
Authors: JScott
Summary: How to use Webchannel-ci

# Webchannel CI

## What is it?

[A Bitbucket repository](https://bitbucket.org/webchannel/webchannel-ci/src). There are a few major sections of code in it: email, log, project-specific, and old. There's also example data in the `test_data` path.

Most things in here should probably be pulled out into a gem or something? It seems awkward to rely on a magic repo being pulled down and used. There's also a lot of cleaning up and refactoring that could be done.

Apologies for everything being so messy D:

### email (deprecated)

Scripts to email test results to the commit author. May or may not still work? Utilizes Amazon SES and thus requires credentials to be filled on deployment.

`log/reset-human-readable-log.rb` is a big part of this as well. It helps to aggregate results for the email. This could be handled a lot better though than some magic script.

### log

Scripts to parse results files and log them to Centralized Logging. For example, `log/phpunit.rb results_directory` will use the class in `lib/phpunit_parser.rb` to pick apart the results and errors file from PHPUnit and send them ElasticSearch and InfluxDB.

### project-specific

The idea of this was scripts that were unique to individual projects. This is actually a bad idea and makes things very opaque at the playbook level. The correct solution would be to pull all of this out and call the appropriate commands inside a Robot Sweatshop job instead. Much more transparent.

### old

This contains old scripts that need updating.

#### archive

Take the results and the code it was run on and dump it into a Git repo as a snapshot artifact of what was run. This is a good idea that no one used so I took it out to reduce complexity. It's also very close to what already happens for the deployment process so seemed potentially redundant.

#### parsing

- TotalValidator, an accessibility tool
- PHPUnit coverage, a PHPUnit result that Rob refused to run because USS code was so broken that it fatally errored out >:|

## How is it used?

Check out the [USS Consumer Build server playbook](https://github.com/telusdigital/playbook-uss-consumer/blob/master/build/playbook.yml) to see it in action:

- Build the code
- Test the code
- Reset the results aggregate
- Log the PHPUnit results
- Log the Git commit data
- Send an email of the results aggregate

It's that easy!
