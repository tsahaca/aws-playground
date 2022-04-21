# Anatomy of a CloudFormation Template

<div style="background-color: rgb(50, 50, 50);">
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
</div>
