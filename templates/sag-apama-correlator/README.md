<!-- Copyright � 2013 - 2018 Software AG, Darmstadt, Germany and/or its licensors

   SPDX-License-Identifier: Apache-2.0

    Licensed under the Apache License, Version 2.0 (the "License");
    you may not use this file except in compliance with the License.
    You may obtain a copy of the License at

        http://www.apache.org/licenses/LICENSE-2.0

    Unless required by applicable law or agreed to in writing, software
    distributed under the License is distributed on an "AS IS" BASIS,
     WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
     See the License for the specific language governing permissions and

     limitations under the License.                                                  

-->

# Apama Correlator

This template can install Apama, create an Apama correlator instance and deploy
a simple Apama application.

This is a reference template that comprehensively demonstrates all possible
correlator configuration that can be applied using a composite template. It
exists for informational purposes only; it is not a well-rounded sample
application that you should build upon.

## Requirements

### Supported Software AG releases

* Apama 10.2 and higher
* Command Central 10.2 and higher

### Supported platforms

All supported Windows and UNIX platforms.

### Supported use cases

* Provisioning of new environments at 10.2 or higher
* Installing latest fixes
* Creating a correlator instance and deploying a simple EPL application to it
* Configuration of:
  * License
  * Ports
  * Logging
  * Persistence
  * All other supported correlator configuration items

## Running as a composite template

When importing the composite template to Command Central, you will have to
attach the simple 'HelloWorld' application. Encapsulate the `template.yaml` and
`HelloWorld.zip` into a single Zip file and import that using the `sagcc`
tooling:

```bash
sagcc exec templates composite import -i template.zip
```

For more information, see [Applying template using Command Central CLI](https://github.com/SoftwareAG/sagdevops-templates/wiki/Using-default-templates#applying-template-using-command-central-cli).

Provision `default` instance of an Apama 10.2 correlator with all the
latest fixes, listening on port 15904:

```bash
sagcc exec templates composite apply sag-apama-correlator nodes=sag1 \
  repo.product=webMethods-10.2 \
  repo.fix=Empower \
  os.platform=LNXAMD64 \
  --sync-job --wait 360
```

## Adding as a runtime layer to a stack

Once imported, this template can also be used as a runtime layer for stacks,
using either the CLI or the web UI.

For more information, see [Creating a stack using Command Central Web UI](https://github.com/SoftwareAG/sagdevops-templates/wiki/Using-default-templates#creating-a-new-stack-using-web-ui).
