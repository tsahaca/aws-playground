# Anatomy of a CloudFormation Template
  
```yaml
AWSTemplateFormatVersion: 2010-09-09 # The only allowable value is 2010-09-09
Description: # Describes the template
Metadata: # Objects providing additional information about the template
Parameters: # Input parameters to pass to your template at runtime
Rules: # A set of rules to validate the parameters provided during creation or update
Mappings: # Key/value pairs used for lookup at runtime
Conditions: # Conditions that control whether certain resources are created or whether properties are assigned values
Transform: # Customizations for serverless applications
Resources: # Defines resources and their properties, the only required top-level object
Outputs: # Values that are returned whenever you view information about the resources created from this template
```
- [Introduction to CloudFormation](https://jennapederson.com/blog/2021/5/10/introduction-to-aws-cloudformation/)

- [PROVISIONING AN EC2 INSTANCE WITH CLOUDFORMATION](https://jennapederson.com/blog/2021/6/21/provisioning-an-ec2-instance-with-cloudformation-part-1/)

[Include diagrams in your Markdown files with Mermaid](https://github.blog/2022-02-14-include-diagrams-markdown-files-mermaid/)

[About mermaid](http://mermaid-js.github.io/mermaid/#/)

Here is a simple flow chart:

```mermaid
graph TD;
    A-->B;
    A-->C;
    B-->D;
    C-->D;
```
```mermaid
graph TB
    sq[Square shape] --> ci((Circle shape))

    subgraph A
        od>Odd shape]-- Two line<br/>edge comment --> ro
        di{Diamond with <br/> line break} -.-> ro(Rounded<br>square<br>shape)
        di==>ro2(Rounded square shape)
    end

    %% Notice that no text in shape are added here instead that is appended further down
    e --> od3>Really long text with linebreak<br>in an Odd shape]

    %% Comments after double percent signs
    e((Inner / circle<br>and some odd <br>special characters)) --> f(,.?!+-*ز)

    cyr[Cyrillic]-->cyr2((Circle shape Начало));

     classDef green fill:#9f6,stroke:#333,stroke-width:2px;
     classDef orange fill:#f96,stroke:#333,stroke-width:4px;
     class sq,e green
     class di orange
```
