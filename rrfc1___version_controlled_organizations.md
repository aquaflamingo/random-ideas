# RRFC1 - Version Controlled Organizations
A fullstack piece of software is an explicitly version controlled (e.g. Git) artifact containing business logic to facilitate a marketable product that is centrally managed and deployed through a hosted provider (e.g. GitHub, IaaS). The benefits of this are that the software is fully searchable and contains historical versions to understand why technical decisions were made and the hosting provider provides a UI abstraction layer to collaborate effectively on change management to the artifact. 

A modern organization is an implicitly version controlled (e.g. tribal know how) artifact containing business logic (e.g. policies, documents and decisions) that provides wrapping context to execute various a subprocesses (e.g. product, marketing, recruiting, operations). It is often uncentrally managed and "deployed" through various hosting providers (e.g.  Jira, Google Documents, Knowledge Management Systems, Registrations). 

Both software and organizations are "iterable truths" ([What is an iterable truth?](https://theportal.group/35-balaji-srinivasan-the-heretic-the-virus/)) that are attempting to rapidly adapt to their respective environments.

**Question**: Is it possible to version control an organization? Could a 21st century organization codify its internal processes, vendors and manage itself in the fashion of a monolithic software repository? 

For example:

```
$ tree

acme.co
-- operations
--- vendors.yml
--- treasury.yml
-- legal
--- incorporation.yml
--- policies.yml 
```

In the same way one uses [Terraform](https://www.terraform.io/) to provision infrastructure and deploy a software application, what if there were a tool that could allow early stage organizations to declaratively write out their non-it infrastructure (legal documents, vendors, banking, company policies, etc) such that there would be a central repository from which their organization is version controlled and "deployed".
