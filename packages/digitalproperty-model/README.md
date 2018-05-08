# Digital Property Network  Model

Defines the Business Network Model for the Digital Property Network.  This is the part of the Business Network Definition that defines the _model file_ that defines the assets, participants, transactions, and relationships that form the Business Network. 

This part is encapulsated within (currently) a single file using a defined syntax. This file itself is encapsulated within an NPM module to permit version and distribution control. The transaction definitions, access control and other functional elements are held within a similar structure (npm module) that is dependant on a version of this model. 

## What should I do with this model
It is expected that the model would be part of the CI pipeline.  It is expected that the model would be held in a source management system, eg github-enterprise. Editted then submitted to a eg TravisCI build. This would then publish the model to the npm-enterpise

This specific DigitalProperty-Model is already published into an NPM repository. Therefore the deployment and pipeline has already been done for you. 

# Creating a new model for yourself
There are two ways of creating a new model; either using the command line and your favourite editor, or by using the the web Composer UI.

## Web Composer UI

_it's coming soon...._ but for the moment use the command line.....

## Command line

*Step1:*  Create a new NPM module 

```
npm init
```

There are no mandatory dependancies that are required; the most important features are name and description of the module. The version number is also very important. This will be used when you construct the full Business Network. That will have a dependancy on a specific version of the model.



*Step2:* Edit the model

The files are simple text files following a defined syntax. Within the npm module directory just create a new file, for example if you were creating this DigitalProperty-Network

```
/git/DigitialProperty-Model> touch models/DigitalLandTitle.cto
```

Load that file up in any editor and you can then add your model, Again using this Digital Property Network the file might contain 
(aside if you are using the Atom editor, then there is a syntax highlighter plugin available)

```
/**  A 'Getting Started Tutorial' to work with the Hyperledger Composer Framework
*/

namespace net.biz.digitalPropertyNetwork

asset LandTitle identified by titleId {
  o String   titleId
  --> Person   owner
  o String   information
  o Boolean  forSale   optional
}

asset SalesAgreement identified by salesId {
  o String    salesId
  --> Person    buyer
  --> Person    seller
  --> LandTitle title
}

participant Person identified by personId {
  o String personId
  o String firstName
  o String lastName
}

transaction RegisterPropertyForSale identified by transactionId{
  o String transactionId
  --> Person seller
  --> LandTitle title
}
```

*Step3:*
The next step is to publish your module to the NPM repository you are using.  So a command along these lines

```
npm publish
```

__That's it... you can now progress to the  DigitalProperty-Network to add the implementation of the the transactions and complete the Business Network Definition creation.__ 

## Advanced things to do with the model
Optional additions here are license checking to ensure that the model meets your Member Organization's agreed standards. 

Other additions:
- Generation of UML to graphically show the assets and relationships
- Validation of the model.

## License <a name="license"></a>
Hyperledger Project source code files are made available under the Apache License, Version 2.0 (Apache-2.0), located in the [LICENSE](LICENSE.txt) file. Hyperledger Project documentation files are made available under the Creative Commons Attribution 4.0 International License (CC-BY-4.0), available at http://creativecommons.org/licenses/by/4.0/.