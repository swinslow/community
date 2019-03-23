# Kubernetes Repository Guidelines

This document attempts to outline a structure for creating and associating
GitHub repositories with the Kubernetes project. It also describes how and when
repositories are removed.

The document presents a tiered system of repositories with increasingly strict
requirements in an attempt to provide the right level of oversight and
flexibility for a variety of different projects.

Requests for creating, transferring, modifying, or archiving repositories can be
made by [opening a request](https://github.com/kubernetes/org/issues/new/choose)
against the kubernetes/org repo.

- [Associated Repositories](#associated-repositories)
  * [Goals](#goals)
  * [Rules](#rules)
- [SIG repositories](#sig-repositories)
  * [Goals](#goals-1)
  * [Rules for new repositories](#rules-for-new-repositories)
  * [Rules for donated repositories](#rules-for-donated-repositories)
- [Core Repositories](#core-repositories)
  * [Goals](#goals-2)
  * [Rules](#rules-1)
- [Removing Repositories](#removing-repositories)
  * [Grounds for removal](#grounds-for-removal)
  * [Procedure for removal](#procedure-for-removal)
- [FAQ](#faq)

## Associated Repositories

Associated repositories conform to the Kubernetes community standards for a
repository, but otherwise have no restrictions. Associated repositories exist
solely for the purpose of making it easier for the Kubernetes community to work
together. There is no implication of support or endorsement of any kind by the
Kubernetes project, the goals are purely logistical.

### Goals

To facilitate contributions and collaboration from the broader Kubernetes
community.  Contributions to random projects with random CLAs (or DCOs) can be
logistically difficult, so associated repositories should be easier.


### Rules

   * Must adopt the Kubernetes Code of Conduct statement in their repo.
   * All code projects use the Apache License version 2.0. Documentation
     repositories must use the Creative Commons License version 4.0.
   * Must adopt the CNCF CLA bot automation for pull requests.


## SIG repositories

SIG repositories serve as temporary homes for SIG-sponsored experimental
projects or prototypes of new core functionality, or as permanent homes for
SIG-specific projects and tools.

### Goals

To provide a place for SIGs to collaborate on projects endorsed by and actively
worked on by members of the SIG. SIGs should be able to approve and create new
repositories for SIG-sponsored projects without requiring higher level approval
from a central body (e.g. steering committee or sig-architecture)

### Rules for new repositories

   * For now all repos will live in `github.com/kubernetes-sigs/\<project-name\>`.
   * Must contain the topic for the sponsoring SIG - e.g.
     `k8s-sig-api-machinery`.  (Added through the *Manage topics* link on the
repo page.)
   * Must adopt the Kubernetes Code of Conduct
   * All code projects use the Apache License version 2.0. Documentation
     repositories must use the Creative Commons License version 4.0.
   * Must adopt the CNCF CLA bot, merge bot and Kubernetes PR commands/bots.
   * All OWNERS of the project must also be active SIG members.
   * SIG membership must vote using lazy consensus to create a new repository
   * SIG must already have identified all of their existing subprojects and
     code, with valid OWNERS files, in
[`sigs.yaml`](https://github.com/kubernetes/community/blob/master/sigs.yaml)

### Rules for donated repositories

The `kubernetes-sigs` organization is primarily intended to house net-new
projects originally created in that organization. However, projects that a SIG
adopts may also be donated.

In addition to the requirements for new repositories, donated repositories must
demonstrate that:

   * All contributors must have signed the [CNCF Individual
     CLA](https://github.com/cncf/cla/blob/master/individual-cla.pdf) or [CNCF
Corporate CLA](https://github.com/cncf/cla/blob/master/corporate-cla.pdf)
   * If (a) contributor(s) have not signed the CLA and could not be reached, a
     NOTICE file should be added referencing section 7 of the CLA with a list of
the developers who could not be reached
   * Licenses of dependencies are acceptable; project owners can ping
     [@caniszczyk](https://github.com/caniszczyk) for review of third party deps
   * Boilerplate text across all files should attribute copyright as follows:
     `"Copyright <Project Authors>"` if no CLA was in place prior to donation

See [the FAQ below](#faq) for more information regarding copyrights and
copyright notices.

## Core Repositories

Core repositories are considered core components of Kubernetes. They are
utilities, tools, applications, or libraries that are expected to be present in
every or nearly every Kubernetes cluster, such as components and tools included
in official Kubernetes releases. Additionally, the kubernetes.io website, k8s.io
machinery, and other project-wide infrastructure will remain in the kubernetes
github organization.

### Goals

Create a broader base of repositories than the existing
gh/kubernetes/kubernetes so that the project can scale. Present expectations
about the centrality and importance of the repository in the Kubernetes
ecosystem. Carries the endorsement of the Kubernetes community.

### Rules

   * Must live under `github.com/kubernetes/<project-name>`
   * Must adopt the Kubernetes Code of Conduct
   * All code projects use the Apache Licence version 2.0. Documentation
     repositories must use the Creative Commons License version 4.0.
   * Must adopt the CNCF CLA bot
   * Must adopt all Kubernetes automation (e.g. /lgtm, etc)
   * All OWNERS must be members of standing as defined by ability to vote in
     Kubernetes steering committee elections. in the Kubernetes community
   * Repository must be approved by SIG-Architecture

## Removing Repositories

As important as it is to add new repositories, it is equally important to prune
old repositories that are no longer relevant or useful.

It is in the best interests of everyone involved in the Kubernetes community
that our various projects and repositories are active and healthy. This ensures
that repositories are kept up to date with the latest Kubernetes wide processes,
it ensures a rapid response to potential required fixes (e.g. critical security
problems) and (most importantly) it ensures that contributors and users receive
quick feedback on their issues and contributions.

### Grounds for removal

SIG repositories and core repositories may be removed from the project if they
are deemed _inactive_. Inactive repositories are those that meet any of the
following criteria:

   * There are no longer any active maintainers for the project and no
     replacements can be found.
   * All PRs or Issues have gone un-addressed for longer than six months.
   * There have been no new commits or other changes in more than a year.
   * The contents have been folded into another actively maintained project.

Associated repositories are much more loosely associated with the Kubernetes
project and are generally not subject to removal, except under exceptional
circumstances (e.g. a code of conduct violation).

### Procedure for removal

When a repository has been deemed eligible for removal, we take the following
steps:

  * Ownership of the repo is transferred to the [kubernetes-retired] GitHub
    organization
  * The repo description is edited to start with the phrase "[EOL]"
  * All open issues and PRs are closed
  * All external collaborators are removed
  * All webhooks, apps, integrations or services are removed
  * GitHub Pages are disabled
  * The repo is marked as archived using [GitHub's archive feature]
  * The removal is announced on the kubernetes-dev mailing list and community
    meeting

This maintains the complete record of issues, PRs and other contributions,
leaves the repository read-only, and makes it clear that the repository should
be considered retired and unmaintained.

## FAQ

**My project is currently in kubernetes-incubator, what is going to happen to
it?**

Nothing. We’ll grandfather existing projects and they can stay in the incubator
org for as long as they want to. We expect/hope that most projects will either
move out to ecosystem, or into SIG or Core repositories following the same
approval process described below.

**My project wants to graduate from incubator, how can it do that?**

Either approval from a SIG to graduate to a SIG repository, or approval from
SIG-Architecture to graduate into the core repository.

**My incubator project wants to go GA, how can it do that?**

For now, the project determines if and when it is GA. For the future, we may
define a cross Kubernetes notion of GA for core and sig repositories, but that’s
not in this proposal.

**My project is currently in core, but doesn’t seem to fit these guidelines,
what’s going to happen?**

For now, nothing. Eventually, we may redistribute projects, but for now the goal
is to adapt the process going forward, not re-legislate past decisions.

**I’m starting a new project, what should I do?**

Is this a SIG-sponsored project? If so, convince some SIG to host it, take it to
the SIG mailing list, meeting and get consensus, then the SIG can create a repo
for you in the SIG organization.

Is this a small-group or personal project? If so, create a repository wherever
you’d like, and make it an associated project.

We suggest starting with the kubernetes-template-project to ensure you have the
correct code of conduct, license, etc.

**Much of the things needed (e.g. CLA Bot integration) is missing to support
associated projects. Many things seem vague. Help!**

True, we need to improve these things. For now, do the best you can to conform
to the spirit of the proposal (e.g. post the code of conduct, etc)

**When I donate my project, am I transferring my copyrights?**

No. All contributors retain ownership of their copyrights in the code they donate.
Instead, they are granting a license to the project (that's the 'L' in 'CLA').

For consistency and efficiency in complying with notice requirements, code that is
donated to a Kubernetes repo should use [the standard header](https://github.com/kubernetes/kubernetes/blob/master/hack/boilerplate/boilerplate.go.txt)
referencing "The Kubernetes Authors". That doesn't mean you are transferring your
copyright. Instead, it's a general reference to the fact that the copyrights remain
owned by the authors of Kubernetes.

Note that you should _never_ modify or remove a third party's copyright notice if
you are not authorized by them to do so.

[GitHub's archive feature]:
https://help.github.com/articles/archiving-a-github-repository/
[kubernetes-retired]: https://github.com/kubernetes-retired
