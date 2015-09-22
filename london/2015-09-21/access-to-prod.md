Managing access to production servers
-------------------------------

In an ideal word access to production is limited to the minimal amount necessary, but determining what that minimal amount is, is hard.

Automated deployments and log aggregation can reduce the need for access to production servers, but when a problem occurs there may still be information not captured by logging or monitoring which can be necessary to diagnose the issue, or changes needed on a machine to fix as quickly as possible. Most people would err on the side of making sure those who needed to fix a production issue had the necessary access.

A common issue is how to consistenly revoke the access of leavers. Privileges tend to accrue over time. 

Long lived instances make access more problematic, there was general agreement on the desirability of short-lived VMs that can be terminated and replaced without manual intervention. Deliberately disrupting service with a Chaos Monkey style of approach can help to ensure that's the case. Where project teams hand-over to a Site Reliability Engineering team, the ability for a system to survive termination of an instance without intervention can and has been used as a hand-over criterion.

SSHing onto the box is not the only issue, AWS accounts and Github also represent attack vectors. It's very easy to grant permissions to the wrong person on Github by accident and an example was given of this actually happening. [gu-who](https://www.theguardian.com/info/developer-blog/2014/apr/11/how-the-guardian-uses-github-to-audit-github) can help with auditing who has access to what in Github, but there was some consensus that a tool for managing Github access based on some file format would be useful.

No great enthusisam for LDAP, but no exciting alternative that anyone had heard of either.

[git-crypt](https://github.com/AGWA/git-crypt) was discussed as a tool for handling credentials in source control, but revoking credentials for leavers is problematic.
