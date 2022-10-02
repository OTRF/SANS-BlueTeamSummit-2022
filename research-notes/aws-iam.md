## [AWS Organization Concept](https://docs.aws.amazon.com/organizations/latest/userguide/orgs_getting-started_concepts.html)

![](https://docs.aws.amazon.com/organizations/latest/userguide/images/AccountOuDiagram.png)

## [How IAM Works](https://docs.aws.amazon.com/IAM/latest/UserGuide/intro-structure.html) 
![](https://docs.aws.amazon.com/IAM/latest/UserGuide/images/intro-diagram%20_policies_800.png)

## IAM Terminologies:
- IAM Resources - user, group , role, policy, identity provider objects
- IAM Identities - resource objects used to identify group e.g. user , group , roles
- IAM Entities - Resource objects that AWS uses for authentications. e.g. users, roles
- Principals - person or application that uses AWS account root user, IAM user, IAM role to sign in . e.g. Federated users and roles


***Lifecycle of IAM Identity***: 

`AWS Account -> IAM User -> Access Keys`

IAM User can be application, not necessarily actual person.

***Federating existing users***: 

Users from Corporate directory -> SAML SSO / Identity broker SSO

- [Federation](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction_identity-management.html#intro-identity-federation) 
![](https://docs.aws.amazon.com/IAM/latest/UserGuide/images/iam-intro-federation.diagram.png)


- [SAML](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_providers_enable-console-saml.html)
![](https://docs.aws.amazon.com/IAM/latest/UserGuide/images/saml-based-sso-to-console.diagram.png)


Internet Users -> ID providers/OpenID Connect ID Provider  

OpenID Connect ID - [Amazon Cognito](https://docs.aws.amazon.com/cognito/latest/developerguide/what-is-amazon-cognito.html)
![](https://docs.aws.amazon.com/cognito/latest/developerguide/images/scenario-cup-cib2.png)

IAM Tutorial - [IAM tutorial: Define permissions to access AWS resources based on tags - AWS Identity and Access Management (amazon.com)](https://docs.aws.amazon.com/IAM/latest/UserGuide/tutorial_attribute-based-access-control.html)

`Create Test User -> Create ABAC Test Policy -> Create Role -> Create Secrets -> View Secret -> Update/Delete Secret`
- Employee sign in with IAM user credential then assume IAM role for team/project. If Federations - can allow to assume a role without IAM user. 
- Same policy attached to all of the roles. Action - allow/deny based on tags
- Can create new resources - only if they attack same tags to resource that are applied to their role.
- Can read resourced owned by team , regardless of project.
- Update/delete resources owned by their team , project
- IAM admin - can add new role for new projects. Admin not required to edit policy to support new project/team.

![](https://docs.aws.amazon.com/IAM/latest/UserGuide/images/tutorial-abac-cross-project.png)



### Roles terms and Concepts:
[Roles terms and concepts - AWS Identity and Access Management (amazon.com)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_terms-and-concepts.html)
Roles and users are both AWS identities with permissions policies that determine what identity can or cannot do in AWS

Role- can be assumed by anyone who needs it. - does not have long term credentials such as password/access keys, instead provide you with temp security credentials for your role session. 
Service linked role ? Role chaining ? Delegation ? 

***Roles:***
- [Roles terms and concepts - AWS Identity and Access Management (amazon.com)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_compare-resource-policies.html)
- [IAM roles - AWS Identity and Access Management (amazon.com)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_compare-resource-policies.html)
- [Monitor and control actions taken with assumed roles - AWS Identity and Access Management (amazon.com)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_compare-resource-policies.html)
- [How IAM roles differ from resource-based policies - AWS Identity and Access Management (amazon.com)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_compare-resource-policies.html)


### IAM ARN: 

arn:partition:service:region:account:resource

Syntax: Region portion blank - since IAM resources are global. 

- arn:aws:iam::account:root  
- arn:aws:iam::account:user/user-name-with-path
- arn:aws:iam::account:group/group-name-with-path
- arn:aws:iam::account:role/role-name-with-path
- arn:aws:iam::account:policy/policy-name-with-path
- arn:aws:iam::account:instance-profile/instance-profile-name-with-path
- arn:aws:sts::account:federated-user/user-name
- arn:aws:sts::account:assumed-role/role-name/role-session-name
- arn:aws:iam::account:mfa/virtual-device-name-with-path
- arn:aws:iam::account:u2f/u2f-token-id
- arn:aws:iam::account:server-certificate/certificate-name-with-path
- arn:aws:iam::account:saml-provider/provider-name
- arn:aws:iam::account:oidc-provider/provider-name


[Unique identifiers](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_identifiers.html):
- Every IAM user has unique ID - even if you reuse friendly name you deleted before.

| Prefix | Resource type               |
| -------| ----------------------------| 
| ABIA	 | [AWS STS service bearer token](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_credentials_bearer.html)|
|ACCA	|Context-specific credential
|AGPA | User group|
| AIDA | IAM user|
| AIPA	| Amazon EC2 instance profile|
| AKIA	| Access key|
| ANPA	| Managed policy|
| ANVA |  Version in a managed policy | 
| APKA | Public key |
| AROA |Role |
| ASCA	| Certificate |
| ASIA  | [Temporary (AWS STS) access key IDs](https://docs.aws.amazon.com/STS/latest/APIReference/API_Credentials.html) use this prefix, but are unique only in combination with the secret access key and the session token. |

### Policies:
- [Managed policies and inline policies - AWS Identity and Access Management (amazon.com)](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies_managed-vs-inline.html#aws-managed-policies)
- [IAM JSON policy elements reference - AWS Identity and Access Management (amazon.com)](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_policies_elements.html)

- Overview of JSON Policy : [Policies and permissions in IAM - AWS Identity and Access Management (amazon.com)](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html#access_policies-json)
- Policy Types: [Policies and permissions in IAM - AWS Identity and Access Management (amazon.com)](https://docs.aws.amazon.com/IAM/latest/UserGuide/access_policies.html#access_policy-types)


### References:
- [Understanding how IAM works - AWS Identity and Access Management (amazon.com)](https://docs.aws.amazon.com/IAM/latest/UserGuide/intro-structure.html)
- [IAM identifiers - AWS Identity and Access Management (amazon.com)](https://docs.aws.amazon.com/IAM/latest/UserGuide/intro-structure.html)
- [AWS account root user credentials and IAM user credentials - AWS General Reference (amazon.com)](https://docs.aws.amazon.com/general/latest/gr/root-vs-iam.html#aws_tasks-that-require-root)
- Services that work with IAM :  [AWS services that work with IAM - AWS Identity and Access Management (amazon.com)](https://docs.aws.amazon.com/IAM/latest/UserGuide/reference_aws-services-that-work-with-iam.html)

- Security Best Practices in IAM : [Security best practices in IAM - AWS Identity and Access Management (amazon.com)](https://docs.aws.amazon.com/IAM/latest/UserGuide/introduction_identity-management.html#intro-identity-first-time-access)

- ExternalId: [How to use an external ID when granting access to your AWS resources to a third party - AWS Identity and Access Management (amazon.com)](https://docs.aws.amazon.com/IAM/latest/UserGuide/id_roles_create_for-user_externalid.html)

CloudTrail: 
- [Logging IAM and AWS STS API calls with AWS CloudTrail - AWS Identity and Access Management (amazon.com)](https://docs.aws.amazon.com/IAM/latest/UserGuide/cloudtrail-integration.html)
- [CloudTrail userIdentity element - AWS CloudTrail (amazon.com)](https://docs.aws.amazon.com/awscloudtrail/latest/userguide/cloudtrail-event-reference-user-identity.html)

## Recommended Reading
- [No more AWS keys for you…. A post about AWS Access keys with… | by Nicole Yip | Engineers @ The LEGO Group | Medium](https://medium.com/lego-engineering/no-more-aws-keys-for-you-8f140de41ec2)
- [IAM Access analyzer — A beginners guide](https://nagwww.medium.com/iam-access-analyzer-a-beginners-guide-6bdc03e007e3)