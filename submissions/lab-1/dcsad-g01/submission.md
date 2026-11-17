# Lab 1 Submission

## Part B

**Error Action Name:** You are not authorized to perform this operation. User: arn:aws:iam::548387266019:user/dcsad-g02 is not authorized to perform: ec2:RunInstances on resource: arn:aws:ec2:ap-southeast-1:548387266019:instance/\*

## Part C

**Policy Statement Blanks:**

- `"Action"`: ec2:RunInstances
- `"Resource"`: instance
- `"ec2:InstanceType"`: t3.micro

## Part D

**Security Group Error Text:** You are not authorized to perform this operation. User: arn:aws:iam::548387266019:user/dcsad-g01is not authorized to perform: ec2:CreateSecurityGroup on resource: arn:aws:ec2:ap-southeast-1:548387266019:security-group/\* because no identity-based policy allows the ec2:CreateSecurityGroup action.

**Running Instance Time:** November 17, 2026, 2:42:54 PM (PHT)

## Part E

**t3.small / Tokyo Denial Error:** You are not authorized to perform this operation. User: arn:aws:iam::548387266019:user/dcsad-g01 is not authorized to perform: ec2:RunInstances on resource: arn:aws:ec2:ap-southeast-1:548387266019:instance/\* with an explicit deny in a permissions boundary: arn:aws:iam::548387266019:policy/umak-lab-boundary.

## Part F Questions

1. Which action did the Part B error name? ec2:RunInstances
2. In your policy, which condition limits `ec2:RunInstances`? The ec2:InstanceType condition with the value t3.micro limits the instance types that can be launched.
3. After you attached `ec2:*` on `*`, why was `t3.small` still denied? Name the boundary statement. The permissions boundary overrides the broad identity policy by explicitly denying instance launches that do not use t3.micro. The boundary statement is DenyAnyInstanceTypeButT3Micro.
4. Why is `ec2:*` on `*` a poor policy even with a boundary? It grants unnecessarily broad EC2 permissions and violates the principle of least privilege. It may allow actions that the user does not need, increasing the risk of accidental or unauthorized changes.
5. In two sentences: what does the boundary control that your policy cannot? The permissions boundary sets the maximum permissions an IAM user can have, regardless of the permissions granted by attached identity policies. It can enforce restrictions such as allowed regions, instance types, resource ownership, and explicit denials that an identity policy cannot override.
