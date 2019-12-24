## Table of Contents

0. Introduction

    0.1 Team Members	

    0.2 Projects	

1. Stakeholders	

    1.1 Potential Privacy & Security Concerns	

    1.3 Ethical Dilemmas	

    1.4 Business Goals	

    1.5 Stakeholders Table	

2. Architecturally Significant Requirements and Utility Tree	

    2.1 Architecturally Significant Requirements	

    2.2 Utility Tree	

    2.3 Quality Attribute Scenarios	

3. Module Overview	

    3.1. Primary Presentation	

    3.2 Element Catalog	

    3.3 Context Diagram	

    3.4 Behaviour Diagram	

    3.5 Interfaces	

    3.6 Rationale	

4. Component & Connector View	

    4.1 Primary Presentation	

    4.2 Element Catalog	

    4.3 Context Diagram	

    4.4 Behaviour Diagram	

    4.5 Interface Documentation	

    4.6 Variability Guide	

    4.7 Rationale	

5. Architecture Assessment, Code Quality and Technical Debt	

    5.1 Code Quality Report
    
    &nbsp;&nbsp;&nbsp;&nbsp;5.1.1 Overview	
    
    &nbsp;&nbsp;&nbsp;&nbsp;5.1.2 Bugs and Vulnerabilities	
    
    &nbsp;&nbsp;&nbsp;&nbsp;5.1.3 Code Smells	
    
    &nbsp;&nbsp;&nbsp;&nbsp;5.1.4 Coverage	
    
    &nbsp;&nbsp;&nbsp;&nbsp;5.1.5 Duplications	
    
    &nbsp;&nbsp;&nbsp;&nbsp;5.1.6 Summary	

    5.2 Architecture Quality Assessment	

6. Pull Request	

7. Conclusion	

8. References	


## 0.0 Introduction

Babel is a community driven project used by many companies and is maintained by volunteers. Babel is a compiler for code in the latest version of JavaScript. It compiles ES6+ syntax into older versions of JavaScript so that older JavaScript engines can run it, making web applications more accessible. Babel can transform syntax, polyfill features that are missing in the target environment, and perform source code transformations [1].

Babel has been developed to run on all browsers, to ensure availability to users. In this document we discuss important aspects of Babel’s. In section 1.0 any potential privacy and security concerns are explained, as well as the business goals, and the stakeholders table. In section 2.0 architecturally significant requirements, the utility tree, and the quality attribute scenarios are discussed here. In section 3.0 the module overview of Babel can be seen, this includes the primary presentation, as well as a context diagram, and a behaviour diagram. In section 4.0 the component and connector overview can be seen, this includes the primary presentation, as well as a context diagram, and a behaviour diagram. In section 5.0 a code quality report can be found analyzing any technical debt present, additionally an architecture quality assessment can be found. In section 6.0 we outline the pull request made to improve Babel. In section 7.0 the conclusion can be found, outlining our findings. Finally, the references that were used are available in section 8.

### 0.1 Team Members

1. Jack Isherwood

2. Dallas Brooks

3. Logan Zetaruk

4. Griffin Storback

5. Isaac Streight

### 0.2 Projects

<table>
  <tr>
    <td>Project Name</td>
    <td>URL</td>
    <td>Language</td>
    <td>KSLOC</td>
    <td>Activity</td>
  </tr>
  <tr>
    <td>Babel</td>
    <td>https://github.com/babel/babel</td>
    <td>JavaScript</td>
    <td>114</td>
    <td>47</td>
  </tr>
</table>


## 1.0 Stakeholders

### 1.1 Potential Privacy & Security Concerns

According to the NPM audit tool, Babel has one, low-level security concern in one of its development dependencies. In *braces*, down the dependency tree from *gulp-watch*, there is a potential Regular Expression Denial of Service (ReDoS) vulnerability. A ReDoS vulnerability denies or reduces services to a web page by submitting a regular expression that takes a long time to evaluate. This issue was patched in *braces* at version 2.3.1. There are no security concerns posted on Babel’s GitHub page.

Because Babel is open source software, security concerns surrounding proper contributions should be considered. The fact that anyone can contribute means anyone can introduce malicious code into the codebase at any time. In Babel’s case, malicious code could either break user confidentiality by observing/monitoring user code from a proprietary system (ACM 1.5) [3], or it could return JavaScript code with different functionality then that which was provided, which could perform some unwanted (and possibly malicious) function not present in the original JavaScript. To mitigate this issue, pull requests should be heavily monitored before being accepted, and pull requests which have already been accepted should contain adequate contact information for whoever was responsible for the code changes.

### 1.3 Ethical Dilemmas

Babel is a tool that has been integrated with many popular software projects and services that have helped the advancement of society. Namely, Facebook Open Source and AirBnb have each contributed $53,000 USD combined to the project since 2017 and 2018 via Open Collective. As a part of these projects’ foundations, Babel has a responsibility to be "good stewards of these systems", as outlined in section 3.7 of the ACM Code of Ethics [3]. This stewardship includes fair access to the system, especially for individuals who may not have easy access to the system; in the case of Babel, this is right along their goal of backwards compatibility. With the lower support for Internet Explorer, especially the decline with the older versions of IE, those without access to modern browsers (or their current versions) are less likely to have full access to advanced systems and their cutting-edge technologies. The use of Babel benefits projects by allowing them to reach a larger audience, but places a responsibility on Babel to maintain this reach with the progression to newer technologies.

With the goal of transpiling code, the projects who use Babel allow access to the raw code to Babel’s core processes. This code could have proprietary knowledge, trade secrets, or details on patented processes (however unlikely in software). With access, Babel has a responsibility to maintain the confidentiality of this information while reading and transpiling the code (ACM 1.5) [3]. Through minification and other similar processes, the information can be handled by Babel effectively while maintaining confidentiality.

### 1.4 Business Goals

Babel’s business goals represent the expectations and requirements needed to satisfy the stakeholders objectives. Babel has the following business goals:

* To stay true to ECMAScript standard.

* To use the least amount of code possible with no dependance of a bulky runtime.

* To have source map support so users can debug with ease.

* For users to be able to easily use a set of plugins.

* To be able to convert to JSX syntax.

* To have support for the latest version of JavaScript through syntax transformations.

* To be able to transform syntax.

* To be able to polyfill features that are missing in a target environment.

* To be able to perform source code transformations.

### 1.5 Stakeholders Table

<table>
  <tr>
    <td>Role</td>
    <td>Concerns</td>
    <td>Instances</td>
  </tr>
  <tr>
    <td>Acquirers</td>
    <td>Oversee the procurement of the system or product</td>
    <td>Babel does not have exact acquirers, but instead sponsors, here we will focus on the top 10: Handshake; trivago; Airbnb; AMP Project; Facebook Open Source; Salesforce; Frontend Masters; RunKit; Webflow; and Adobe.</td>
  </tr>
  <tr>
    <td>Assessors</td>
    <td>Oversee the system’s conformance to standards and legal regulation</td>
    <td>From a legal perspective, Babel adheres to the MIT License, which can be found here: https://github.com/babel/babel/blob/master/LICENSE </td>
  </tr>
  <tr>
    <td>Communicators</td>
    <td>Explain the system to other stakeholders via its documentation and training materials</td>
    <td>Babel is very active on its own slack channel, as well as it has a twitter account where users can ask questions. The main communicator is the @babeljs account.</td>
  </tr>
  <tr>
    <td>Developers</td>
    <td>Construct and deploy the system from specifications (or lead the teams that do this)</td>
    <td>Babel has 825 contributors, here we will focus on the top 10: @sebmck; @hzoo; @loganfsmyth; @existentialism; @danez; @nicolo-ribaudo; @marijnh; @rreverser; @jamiebuilds; and @amasad</td>
  </tr>
  <tr>
    <td>Maintainers</td>
    <td>Manage the evolution of the system once it is operational</td>
    <td>There are 7 core maintainers: Babel; D. Tschincer; B. Ng; L. Smyth; N. Ribaudo; S. Sauleau; and H. Zhu.</td>
  </tr>
  <tr>
    <td>Production Engineers</td>
    <td>Design, deploy, and manage the hardware and software environments in which the system will be built, tested, and run</td>
    <td>Not available for this project.</td>
  </tr>
  <tr>
    <td>Suppliers</td>
    <td>Build and/or supply the hardware, software, or infrastructure on which the system will run</td>
    <td>Not available for this project.</td>
  </tr>
  <tr>
    <td>Support Staff</td>
    <td>Provide support to users for the product or system when it is running</td>
    <td>This would be the support community:
	    
* https://babeljs.slack.com/  

* https://stackoverflow.com/questions/tagged/babeljs 

* https://twitter.com/babeljs</td>   
  </tr>
  <tr>
    <td>System Administrators</td>
    <td>Run the system once it has been deployed</td>
    <td>Not available for this project.</td>
  </tr>
  <tr>
    <td>Testers</td>
    <td>Test the system to ensure that it is suitable for use</td>
    <td>This would be the same as maintainers and developers.</td>
  </tr>
  <tr>
    <td>Users</td>
    <td>Define the system’s functionality and ultimately make use of it</td>
    <td>This would be a variety of users, from developers looking to contribute to Babel, to anyone wanting to transpile old version of javascript</td>
  </tr>
</table>


## 2.0 Architecturally Significant Requirements and Utility Tree

### 2.1 Architecturally Significant Requirements

<table>
  <tr>
    <td>ASR</td>
  </tr>
  <tr>
    <td>All pushes must be reviewed in less than 5 days.</td>
  </tr>
  <tr>
    <td>A new stable version must be pushed every 3 months.</td>
  </tr>
  <tr>
    <td>There must be no more than 150 non-critical issues reported per month.</td>
  </tr>
  <tr>
    <td>New features must be learnable in less than 1 day.</td>
  </tr>
  <tr>
    <td>All critical bugs must be fixed in less than 3 days.</td>
  </tr>
  <tr>
    <td>All non-critical bugs must be fixed in less than 2 weeks.</td>
  </tr>
  <tr>
    <td>The newly created transpile is 99.999% error free.</td>
  </tr>
  <tr>
    <td>The system can transpile in less than 100ms.</td>
  </tr>
</table>


### 2.2 Utility Tree

![Utility Tree](images/utility.png)

Figure 1. Utility Tree

### 2.3 Quality Attribute Scenarios

QAS: Performance

<table>
  <tr>
    <td>Aspect</td>
    <td>Details</td>
  </tr>
  <tr>
    <td>Scenario Name</td>
    <td>Accurate Transpilation</td>
  </tr>
  <tr>
    <td>Business Goals</td>
    <td>The users have the goal that babel will reliably compile their JavaScript to run on all browsers.</td>
  </tr>
  <tr>
    <td>Quality Attributes</td>
    <td>Performance</td>
  </tr>
  <tr>
    <td>Stimulus Source</td>
    <td>A user</td>
  </tr>
  <tr>
    <td>Stimulus</td>
    <td>The user calls babel to transpile their source code.</td>
  </tr>
  <tr>
    <td>Response</td>
    <td>Babel reads the source and outputs transpiled code into a build directory.</td>
  </tr>
  <tr>
    <td>Response Measure</td>
    <td>The transpiled output JavaScript functions exactly as the source would at least 99.999% of the time.</td>
  </tr>
</table>


QAS: Maintainability

<table>
  <tr>
    <td>Aspect</td>
    <td>Details</td>
  </tr>
  <tr>
    <td>Scenario Name</td>
    <td>Issue Resolution</td>
  </tr>
  <tr>
    <td>Business Goals</td>
    <td>Developers have the goal of improving Babel, and users have goals that the software will be issue free.</td>
  </tr>
  <tr>
    <td>Quality Attributes</td>
    <td>Maintainability</td>
  </tr>
  <tr>
    <td>Stimulus Source</td>
    <td>Developer or User</td>
  </tr>
  <tr>
    <td>Stimulus</td>
    <td>The person who finds the issue reports it to the GitHub repository by opening a new issue.</td>
  </tr>
  <tr>
    <td>Response</td>
    <td>A Babel developer sees the issue, assigns it, it gets fixed and then closed.</td>
  </tr>
  <tr>
    <td>Response Measure</td>
    <td>The issue should be closed within 2 weeks if they are non-critical and with 3 days if they are critical.</td>
  </tr>
</table>


QAS: Modifiability

<table>
  <tr>
    <td>Aspect</td>
    <td>Details</td>
  </tr>
  <tr>
    <td>Scenario Name</td>
    <td>Pull Request Reviews</td>
  </tr>
  <tr>
    <td>Business Goals</td>
    <td>The developer goal of improving Babel</td>
  </tr>
  <tr>
    <td>Quality Attributes</td>
    <td>Modifiability</td>
  </tr>
  <tr>
    <td>Stimulus Source</td>
    <td>Babel Developer</td>
  </tr>
  <tr>
    <td>Stimulus</td>
    <td>A developer writes some code to improve babel and opens a new pull request.</td>
  </tr>
  <tr>
    <td>Response</td>
    <td>Another developer with the required permissions reviews and either approves the pull request or requests changes.</td>
  </tr>
  <tr>
    <td>Response Measure</td>
    <td>A pull request should be reviewed and decided within 3 days of it being added.</td>
  </tr>
</table>


## 3.0 Module Overview

### 3.1. Primary Presentation

A module view shows the elements of Babel, and their relations. This diagram demonstrates what dependencies exist between modules, and which are necessary to Babel. The primary presentation of Babel is built focusing primarily on the quality attribute scenarios from Milestone 2.

![primary presentation](images/primary_presentation.png)

Figure 2. Module View and Primary Presentation Diagram

### 3.2 Element Catalog

This section describes and expands on the primary presentation of Babel, as shown in Figure 1.

**Babel**

The Babel module is the main application in which all other internal modules operate, and also interacts with the external modules. The main logic of Babel is demonstrated in the diagram above. Most of Babel’s features are self-contained, with many modules intrinsically interconnected.

**core**

The core module holds the main methods of Babel, transforming code both as a file and as source code. Therefore, core is reliant on many of the other modules in Babel.

**helper-fixtures**

The helper-fixtures module is in charge of running tests on the transpiled JavaScript code, comparing the actual output to the expected output.

**babel-cli**

The babel command line interface module provided by Babel is used to compile files from the command line. Plug-ins and piping features are supported.

**babel-node**

The babel-node module adds the Babel preset and plugins to a Node.js command line interface.

**babel-register**

The register module will bind itself to the node and automatically compile files on the fly.

**polyfill**

The polyfill module is used to emulate a full ES2015+ environment for the reverse compatibility requirement of Babel.

**code-frame**

The code-frame module is in charge of highlighting the syntax of JavaScript code for the terminal.

**babel-traverse**

The traverse module is responsible for maintaining the overall abstract syntax tree state, as well as replacing, removing, and adding nodes.

**babel-generator**

The generator module transforms the final abstract syntax tree back into a string of JavaScript code, at the same time creating source maps.

**babel-parser**

The parser module parses the code with respect to ECMAScript 2017. It supports JSX, Flow, and Typescript styles, and it can additionally transcribe comments.

**eslint-plugin-development**

The eslint-plugin-development module is a tool to enforce a set of rules on Babel plug-ins so that best coding practices are maintained. This can reduce usability errors in third-party plug-ins.

### 3.3 Context Diagram

This diagram shows how the Babel application depends on its environment.

![context diagram](images/context.png)

Figure 3. Context Diagram

### 3.4 Behaviour Diagram

 The following sequence diagram shows the behavior of the Babel system when a user invokes it through the Babel CLI. To initialize, the system uses: the command line arguments from the CLI, ENV, ‘babel.config.js’, and ‘.babelrc’. After initialization the system loads the input file and begins the transpilation process. The transpilation process involves 3 steps: parsing, traversal, and generation. Parsing involves converting the input code, in this case ‘script.js’, and converting it into its abstract syntax tree (AST) representation. The traversal step takes the AST from step one and recursively traverses through it, transforming to represent an AST that will represent the transpiled code. The final step that Babel performs is generation, this step takes the transformed AST and generates valid JavaScript code.

#### Elements

**ENV**

Users can use environment variables in their Babel configurations. ENV is shorthand for the users environment variables.

**babel.config.js**

babel.config.js is a project-wide configuration file for Babel. Babel automatically looks for this file in the user’s project root.

**.babelrc**

.babelrc is a configuration file for Babel that can be used to create different configurations of Babel based on different parts of the project. Babel looks for this file by searching up project file structure starting from the file being transpiled.

**script.js**

script.js is a placeholder name for the JavaScript file that is being transpiled in the example.

![behaviour diagram](images/behaviour.png)

Figure 4. Behaviour Diagram

### 3.5 Interfaces

Interface 1: babel-cli

<table>
  <tr>
    <td>Interface Identity</td>
    <td>Babel Command Line Interface</td>
  </tr>
  <tr>
    <td>Resources Provided</td>
    <td>String babel(in script.js)
Pre-conditions:
script.js file must exist and be a valid JavaScript file.
Post-conditions:
On success, the command line will output the transformed code to stdout.

void babel(in script.js, in script-compiled.js)
Pre-conditions:
script.js file must exist and be a valid JavaScript file.
Post-conditions:
On success, the transformed code will be placed in the provided output file (script-compiled.js).</td>
  </tr>
  <tr>
    <td>Data Types</td>
    <td>Input:
The input is a JavaScript file or set of JavaScript files, which Babel treats as a string.
Output:
Using the Babel CLI command, the output type is a string, and outputs to a specified file, or if no file is provided, outputs through stdout.</td>
  </tr>
  <tr>
    <td>Error Handling</td>
    <td>When a faulty JavaScript file is provided, the Babel parser will stop execution and throw a standard JavaScript error corresponding to whichever aspect of the JavaScript file was faulty.</td>
  </tr>
  <tr>
    <td>Quality Attributes</td>
    <td>Simplicity:
As Babel is mostly used as a project dependency, the Babel CLI should remain simple and easy to use, and should reflect regular system functionality.</td>
  </tr>
  <tr>
    <td>Rationale</td>
    <td>The main use of Babel comes from using it as a dependency within a project. The Babel CLI helps users singularly transpile JavaScript files, and is a useful tool for testing during plug-in development. It also serves as a nice entrypoint to system behaviour for new users.</td>
  </tr>
  <tr>
    <td>Usage Guide</td>
    <td>$ babel script.js
$ babel script.js --out-file script-compiled.js</td>
  </tr>
</table>


Interface 2: babel-traverse

<table>
  <tr>
    <td>Interface Identity</td>
    <td>traverse(AST, transformation)</td>
  </tr>
  <tr>
    <td>Resources Provided</td>
    <td>void traverse(in AST, in transformation(path))
Pre-conditions:
AST must be a tree associated with a valid JavaScript file, which as long as babel-parser has succeeded, it ought to.
The transformation(path) function must be valid JavaScript.
Post-conditions:
On success, the path parameter to the provided transformation function will contain the transformed AST.</td>
  </tr>
  <tr>
    <td>Data Types</td>
    <td>AST:
ASTs are tree representations of the abstract syntactic structure of source code (Babel’s AST spec: https://github.com/babel/babel/blob/master/packages/babel-parser/ast/spec.md).
transformation(path):
transformation(path) is a function consisting of code for specific transformations - it’s parameter path is the object where the resulting transformed AST will be put.</td>
  </tr>
  <tr>
    <td>Error Handling</td>
    <td>The traverse module throws an error when the transformation function contains faulty syntax.</td>
  </tr>
  <tr>
    <td>Quality Attributes</td>
    <td>Reliability:
As the traverse module actually performs the intended modifications to source code, it is at the heart of the application and should always function in a predictable manner.</td>
  </tr>
  <tr>
    <td>Rationale</td>
    <td>The simple syntax for the traverse function allows for an easily legible way of transforming an AST. The traverse module must be reliable and consistent, in order for plug-in developers to be able to trust that each traversal will be thorough and will produce predictable changes to the AST.</td>
  </tr>
  <tr>
    <td>Usage Guide</td>
    <td>traverse(AST, {
enter(path) {
// do any needed transformations to the AST
}
});</td>
  </tr>
</table>


### 3.6 Rationale

Babel is a JavaScript transpiler, allowing the use of modern JavaScript syntax with older browsers. Babel allows developers to use the JavaScript tricks and tools while providing backwards compatibility to not limit a project’s consumer base or restrict a project’s use of new language features. In Babel 6, there was no separation between the components of Babel: babel-core, babel-cli, and most everything else was lumped into one package. With the current Babel 7 architecture, the project is decomposed into smaller, less coupled modules. This decomposition of Babel improves multiple quality attributes: modifiability, performance, and usability.

In Babel 7, the main components that make up Babel are split up from the monolith in Babel 6. This separation of distinct components allows each component to grow with less of a concern for the inadvertent effects on the others. The features of a component can be exposed as desired via defined interfaces. An example is the separation of babel-parser and babel-generator: the parser produces an AST and the generator consumes an AST. These components still have a relation between then, but it’s not a funnel from one immediately to the other.

With the componentization of Babel, this offers points of improvement in performance and lays the foundation for future upgrades. Under-the-hood improvements for each component don’t require touches in neighbouring components, allowing developers to target performance tweaks in finer detail. The use of components reduces the length of paths throughout the application, passing through only the components required to complete the specific case.

Most notable in the babel-cli and babel-core modules, Babel 7 offers an improvement in usability. With options as both a command line tool and an in-project dependency, this offers methods of interacting with Babel for a wide variety of projects and users. This holds for componentized architecture: components can be used as independent tools. Previous to Babel 7, these options were poorly defined and the lines between components were blurred, making use of portions of Babel in isolation difficult to use.

## 4.0 Component & Connector View

### 4.1 Primary Presentation

The style used for the component and connector view is Pub-Sub one, which helps better represent the architecture of Babel. Babel relies on the babel-parser component to be more effective and efficient in performing tasks. This primary presentation of Babel is built focusing primarily on the quality attribute scenarios from Milestone 2.

![primary presentation](images/m4_primary_presentation.png)

Figure 5. Component & Connector View and Primary Presentation

### 4.2 Element Catalog

This section describes and expands on the primary presentation of Babel, as shown in Figure 1.

**babel-parser/parse**

Parse is the interface from babel-parser to its consumers. This module is exported as a function with which the Core and Helper-Fixtures nodes can use the services provided by the Parser module. This is the entry point to the Parser module: in addition to internal helper functions, the Parse interface is effectively a wrapper for a Parser class instance.

**babel-parser/parser**

The Parser component is the primary class of Parser node. With dependencies on helpers within the Parser node, the Parse class transforms a file with the ES2015+ features to ES2015 compliant code using Babel’s Abstract Syntax Tree (AST) structures.

**babel-parser/options**

The Options component is a list of qualifiers of the starting point of each AST, highlighting the source filename, file plugin list, JavaScript strictMode functionality, and other file structure decisions that affect compilation.

**babel-parser/plugin-utils**

The Plugin-Utils component organizes the plugins used by the parsed file. This component is responsible for finding the described plugin, validating the plugin and its decorators, and staging the plugins to be inserted into the file and imported by the module.

**helper-fixtures/template**

The Template component also uses the Parse interface. The AST generated from the input file is then validated and traversed to build metadata.

**babel-core/transformation**

The Babel Core Transformation uses the Babel Parser to normalized target files. These functions validate the plugins used by the parsed file and their compatibility with Babel Core.

**babel-core/config**

The part of the Core config file used related to parsing is the PluginPasses object type to complete the transformation part of Babel Core for listing the plugins used by the parsed file.

**lodash**

lodash is an NPM package used for dealing with default JavaScript types: arrays, object, etc. In the Babel Core transformation, Lodash provides a deep clone method to copy the object-representation of the generated AST.

**Path**

The JavaScript Path package is a way to interact with files and directories. The module is used by Babel Core to find the list of directories in which the transformed file is stored.

### 4.3 Context Diagram

During runtime the only external nodes that interact with ‘babel-parser’ are the ‘babel-core’ and ‘helper-fixtures’ nodes. In both of these cases ‘babel-parser’ is invoked using the method ‘babel-parser.parse(code, [options])’. This method takes the code to be transpiled and an options object as arguments and returns the parsed AST.

![context diagram](images/m4_context.png)

Figure 6. Context Diagram

### 4.4 Behaviour Diagram

The following diagram shows the behaviour of the ‘babel-parser’ when accessed through the ‘parse(code, [options])’ interface. The diagram starts when babel-core calls ‘parse(code, [options])’ where code is the source code to be parsed and ‘[options]’ is a set of optional configurations. The ‘validatePlugins(options.plugins)’ call is only executed if plugins are included in the options object, the purpose of this function is to validate the included plugins. On error ‘validatePlugins’ throws an exception, otherwise returns nothing. Both ‘Parser’ and ‘Options’ in the diagram represents objects of their own respective types. Once the ‘Parser’ object has been initialized, ‘Parser.parse()’ is called which parses the code and returns the parsed abstract syntax tree (AST).

![behaviour diagram](images/m4_behaviour.png)

Figure 7. Behaviour Diagram

### 4.5 Interface Documentation

Interface 1: babel-parser

<table>
  <tr>
    <td>Interface Identity</td>
    <td>parse(code, [options])</td>
  </tr>
  <tr>
    <td>Resources Provided</td>
    <td>babelParser.parse(in code, in [options])
Pre-conditions:
code must be a string consisting of valid JavaScript.
The options mentioned in [options] must correspond to alterable options (see list of options here https://babeljs.io/docs/en/babel-parser#options).
Post-conditions:
On success, parse generates and returns an AST according to Babel’s AST spec (https://github.com/babel/babel/blob/master/packages/babel-parser/ast/spec.md).

babelParser.parseExpression(in code, in [options])
Pre-conditions:
code must be a string consisting of a single valid JavaScript expression.
The options mentioned in [options] must correspond to alterable options.
Post-conditions:
On success, parseExpression generates and returns an AST according to Babel’s AST spec for a single given expression.</td>
  </tr>
  <tr>
    <td>Data Types</td>
    <td>code:
code is a string containing the JavaScript syntax which should be transformed into an AST.
[options]:
A set of alterable fields, defined explicitly unless the default behaviour is desired. Each option mentioned in [options] must correspond to an actual alterable value (e.g. "plugins", “sourceType”, etc. - see https://babeljs.io/docs/en/babel-parser#options for full list of available options).</td>
  </tr>
  <tr>
    <td>Error Handling</td>
    <td>When an error is found in the provided JavaScript syntax babel-parser will throw an error. However, if the “errorRecovery” option is set to true, the parser will continue, generating an AST with an “errors” property representing an array of all the parsing errors.</td>
  </tr>
  <tr>
    <td>Quality Attributes</td>
    <td>Reliability:
As the babel-parser is in charge of tokenizing the input code, it must be predictable and should handle all edge cases appropriately.</td>
  </tr>
  <tr>
    <td>Rationale</td>
    <td>The babel-parser module was designed to be simple and reliable, and so doesn’t allow for much customizability in terms of plugins. The plugins provided (see https://babeljs.io/docs/en/babel-parser#plugins) allow for different flavours of JavaScript to be parsed, such as JSX and Typescript syntax.</td>
  </tr>
  <tr>
    <td>Usage Guide</td>
    <td>require("@babel/parser").parse("code", {
sourceType: "module",

plugins: [ "jsx" ]
});</td>
  </tr>
</table>


Interface 2: helper-fixtures/template

<table>
  <tr>
    <td>Interface Identity</td>
    <td>template(code, [options])</td>
  </tr>
  <tr>
    <td>Resources Provided</td>
    <td>template(in code, in [options])
Pre-conditions:
code must be a string consisting of valid JavaScript.
The placeholders in code must be either syntactic placeholders or identifier placeholders, depending on which was specified in [options].
The options mentioned in [options] must correspond to alterable options (the template module accepts the same options as the parser module, see here https://babeljs.io/docs/en/babel-parser#options).
Post-conditions:
On success, template returns a function which is invoked with an optional object of replacements.</td>
  </tr>
  <tr>
    <td>Data Types</td>
    <td>code:
code is a string containing the JavaScript syntax which should be transformed into an AST. It may contain either syntactic or identifier placeholders, depending on the value of the "syntacticPlaceholder" option within [options].
[options]:
A set of alterable fields, defined explicitly unless the default behaviour is desired. Each option mentioned in [options] must correspond to an actual alterable value (e.g. “plugins”, “sourceType”, etc. - see https://babeljs.io/docs/en/babel-parser#options for full list of available options).</td>
  </tr>
  <tr>
    <td>Error Handling</td>
    <td>Template will throw an error if the wrong placeholder syntax is used. Because template uses babel-parser, after creating a template and using it to parse an AST, babel-parser will find JavaScript syntax errors.</td>
  </tr>
  <tr>
    <td>Quality Attributes</td>
    <td>Simplicity:
Since it functions by using babel-parser with the added functionality of filling in placeholders, it should be simple to use, and should resemble the parse function itself.
Reliability:
As it is essentially another way to use babel-parser, it should be as predictable as possible, and should never misplace or misinterpret defined placeholders.</td>
  </tr>
  <tr>
    <td>Rationale</td>
    <td>Babel’s template module was designed in order to allow for the usage of placeholders within the provided code to be parsed. Using the babel-parser module, it closely resembles the parse function itself, and uses the same options, which allows for easier understanding of the functions usage.</td>
  </tr>
  <tr>
    <td>Usage Guide</td>
    <td>// Template is created with placeholders importName and source.
const buildRequire = template(`var %%importName%% = require(%%source%%);`);

// Template is used, injecting values into the designated placeholders.
const ast = buildRequire({
importName: t.identifier("myModule"),
source: t.stringLiteral("my-module"),
});</td>
  </tr>
</table>


### 4.6 Variability Guide

Babel can be used with a variety of plugins, but it is important to note that this can change the behaviour of Babel. Out of the box Babel doesn’t do anything, plugins need to be added in order to make Babel useful. Without plugins it basically acts like const babel = code => code; by parsing the code and then generating the same code back out again.

**Plugins**

In Babel, users can add either individual plugins, or can enable a set of plugins in a preset. Users can add different types of plugins, for example: transform plugins, which add transformations directly to the code, as well as the corresponding syntax plugins; syntax plugins, which are only used to allow Babel to parse specific types of syntax. If no plugins are added Babel can not not do anything, other than return the same code back, but once plugins are added Babel becomes a lot more powerful. If a specific plugin in is in npm, the name of the plugin can be passed to Babel, and Babel can check if it is installed in node_modules. Plugins can also be referenced in shorthand if they are already installed, then they can be referenced without babel-plugin-, this allows the user to write quicker code and not have to worry about using specific prefixes. Babel has many different plugins which allow Babel to perform at its full potential, but all need to be installed by the user. Babel is as strong as the user allows it to be, which can drastically change how Babel may operate.

### 4.7 Rationale

Since Babel is a transpiler, it is crucial that Babel be able to correctly parse the incoming code from newer JavaScript formats into JavaScript that is compatible with older browsers. That is what Babel is designed to do, after all. In the Babel 7 architecture, this is handled by the babel-parser component which is used solely by the babel-core and helper-fixture classes. Since only two other components use the parser, Babel’s transpiling mechanisms can be modified with relative ease. In fact, this was recently done when Babel upgraded their transpiling service from Babylon to their own current babel-parser.

The simple design of the parse functionality helps users easily use the program. Through babel-core or the helper-fixtures, the user sends only their code and (optional) options and babel-parser returns an Abstract Syntax Tree. The AST is vital to transpiling, as the new JavaScript is derived from this tree. A simple command makes babel easily accessible, but powerful and deep to users that need extensive functionality.

An AST is used to parse JavaScript because the form of the code is preserved. Priority and assignments happen in the same order they would in the original code. This allows the code to be rebuilt easily through a tree traversal, substituting methods and expressions as needed. A good example of this is shown on Babel’s website:

```
[1, 2, 3].map(n => n ** 2);
```
becomes
```
[1, 2, 3].map(function (n) {
	return math.pow(n, 2);
});
```

This example is easy to follow and shows the power of babel-parser. The arrow function that is supported in next-gen JavaScript has been downgraded to a function that is readable by older JavaScript versions. The statement itself has been rebuilt, but the data has not been modified and the intent of the code has not changed.

## 5.0 Architecture Assessment, Code Quality and Technical Debt

### 5.1 Code Quality Report

SonarQube was used to evaluate Babel’s code quality. SonarQube was helpful in identifying potential technical debt that needs to be addressed. SonarQube is an automated code analysis tool that provides an overview of certain issues such as: identifying bugs, vulnerabilities, code smells, coverage, and duplications within a project. SonarQube also provides a quality gate of whether the project status passes its set of measures in order to be deployable or not. SonarCloud provides its own Quality Gate. A Quality Gate is a set of measure-based boolean conditions, and helps to know if the project is production-ready. The Quality Gate checks the project against reliability, security, maintainability, coverage, and duplications thresholds. In SonarCloud, a bug is "a coding error that will break your code and needs to be fixed immediately,'' security is “code that can be exploited by hackers," maintainability is “the estimated time it will take to fix all code smells,” coverage is “the percentage of lines of code covered by tests,” and duplications which are “identical lines of code.”

![quality gate](images/QualityGate.png)

Figure 8. Quality Gate

#### 5.1.1 Overview

When Babel was run through SonarCloud, it passed the Quality Gate and received a "D" in reliability, and an “A” in both security and maintainability. Reliability was rated as “D” because the Quality Gate reported at least one bug it classified as critical, security was rated “A” as no vulnerabilities were detected, and maintainability was rated “A” because the technical debt ratio was less than 5%. Babel was reported having 18 bugs, 0 vulnerabilities, 36 security hotspots, 3 days of technical debt, 242 code smells, 81.1% coverage, 1.6% duplications, and 57 duplicated blocks.

The SonarCloud instance report can be found here: [https://sonarcloud.io/dashboard?id=jackisherwood_babel](https://sonarcloud.io/dashboard?id=jackisherwood_babel)

#### 5.1.2 Bugs and Vulnerabilities

One bug was reported on line 8 in the packages/babel-core/src/config/files/index.js file. The cause of this bug is "Expected an assignment or function call and instead saw an expression." This message was a result of a bug that found an expression, when a function was expected. The comment above line of code that caused the major bug warning starts with “kind of gross […]”, this is an example of deliberately introducing technical debt. This expression works for now, but is hacky and needs to be changed. Some of these are notes for future versions of Babel, SonarCloud found no vulnerabilities, but 36 security hotspots. SonarCloud defines security hotspots as: “Security-sensitive code that requires manual review to assess whether or not a vulnerability may exist.” This implies that the developers in charge of security may need to review these potential vulnerabilities. Most of these security vulnerabilities are making sure that command line arguments are being used safely.

![Bugs and Vulnerabilities](images/SpecificBug.png)

Figure 9. Bugs and Vulnerabilities

#### 5.1.3 Code Smells

SonarCloud defines "code smells" as “code that is confusing and difficult to maintain.” SonarCloud found 242 code smells in Babel, 5 are block, 47 are minor, 189 are major, and 1 is critical. The blocker code smells were all issues with how switch cases were ended, in the packages/bable-parser/src/tokenizer/index.js file. The minor code smells were primarily suggestions to rename files, while the major code smells were mostly that some variable was already previously defined in an upper scope. The critical code smell was that the default clause needed to be moved to the end of the switch statement. The estimated time to fix a blocker code smell was marked at 10 minutes, a minor code smell was 5 minutes, a major code smell varied from 5 to 30 minutes, and a critical code smell was marked at 5 minutes. SonarCloud estimated that it would take 3 days to fix all found code smells. This isn’t a lot of technical debt, but 195 of all 242 code smells were marked as either blocker, major, or critical, and need to be fixed soon.

![Code Smells](images/CodeSmells.png)

Figure 10. Code Smells

#### 5.1.4 Coverage

SonarCloud’s Quality Gate reported that the coverage was 81.1%, this means that Babel can sufficiently test the majority of its code. Each major component of Babel contains its own testing folder that ensures that each corresponding component meets the minimum requirements necessary to be deployment-ready.

#### 5.1.5 Duplications

Babel was found to have 1.6% duplication, which was 1295 line of duplicated code, or 57 duplicated blocks. Having many duplications in a project may poorly impact the overall performance, as it adds unnecessary compile time. The packages/babel-types/src/validators/generated/index.js file was found to have the highest percentage of duplications in Babel, at 34 duplicated blocks. The next highest percentage of duplication was the packages/babel-preset-env/data/corejs2-built-in-features.js file, with 19 duplicated blocks.

![Duplications](images/Duplications.png)

Figure 11. Duplications

#### 5.1.6 Summary

After using SonarQube to analyse Babel, it was discovered that the code quality could be enhanced by improving reliability. Babel passed the Quality Gate, but the area that needed the most focus was the reliability section, which received a "D". Babel’s reliability could be improved by reducing complexity, being consistent with naming conventions, and by removing any unnecessary duplications. Maintainability was identified as an important quality attribute for Babel. Maintainability could be improved by removing any major code smells, this would allow for developers to have an easier time contributing to Babel.

### 5.2 Architecture Quality Assessment

The Quality Attribute Scenario used to evaluate Babel will be centred around the number of open pull requests related to technical debt and the in-code admissions of technical debt. For this, an admission of technical debt will be an area where the developer noted the current implementation is insufficient, even though it may work, through keywords like "fix", “todo”, or “hack”.

The SonarCloud analysis of Babel is that the technical debt is due to the bugs found and the uncovered tests. Since Babel is compartmentalized into packages, instead of the whole project having test specifications, each individual component has their own suite of test specifications. With this, there is more than the 81.1% test coverage, as outlined by SonarCloud. We will not focus on this area of potential technical debt because, while is can be improved, this is a significant amount of testing done by Babel. The code added in the last 30 days improves in this area with 100% coverage, as per SonarCloud.

Bugs in babel are mostly renamed, or reused variables. In fact, the package with the most bugs (packages/babel-traverse/src/path/index.js, with 6 out of the 18 total reported bugs) is an export class that works similar to a constructor. These supposed bugs are all of the "Remove or rename duplicate property" variety, yet those names are integral to the performance of the package. SInce SonarQube only checks for constructor classes, this export class is missed. Other bugs in Babel are typically argument mismatch types, where SonarQube reports “This function expects 1 argument, but 2 were provided.” Since JavaScript simply ignores the extra argument, the code works fine at the moment, but these types of bugs are more serious and should be dealt with accordingly.

There are 58 instances of the word "todo" in Babel. A few of the todo comments have no additional text associated with them, they’re just a flag. This doesn’t provide any insight as to why the implicitly referenced chunk of code needs to be refactored to remove the technical debt. To anyone trying to remove this technical debt, other than the author of the todo, will have no specific knowledge as to why the code needs to be refactored. [This section of code](https://github.com/babel/babel/blob/87feda7c2a33b7bde6dc926ced4dd741a90cc860/packages/babel-parser/src/tokenizer/index.js#L154), in the Babel tokenizer, has a todo surrounding a method called match. Initially, the method does not seem like debt, returning the result of a comparison between the parameter type and an object property type. However, it has been flagged as debt, but there is no other indication. Other todo’s reference changes for the upcoming version of Babel (Babel 8), renaming variables, splitting up methods, and [lines that aren’t completely understood](https://github.com/babel/babel/blob/b6486a22cbbb0eb1482f0d2a6340b52d5ac5bee0/packages/babel-plugin-transform-destructuring/src/index.js#L607).

In Babel’s pull request structure, there aren’t any labels that explicitly indicate technical debt. However, there are two main labels that relate to issues that involve technical debt: "internal" and “polish”. The polish label is mainly changes that are nice to have, such as optimized outputs to removing function that exists for backwards compatibility. While some have more impact than others, these changes aren’t aimed at fixing bugs or adding new features; they’re aimed at making the code easier to read and maintain. The internal label is filled with pull requests with how Babel is viewed in-house. The most recent pull request changes “babel-eslint-config-internal” to “@babel/eslint-config-internal”, updating from old naming conventions and providing improved consistency across the project. Another fixes a bug in the test runner. A third adds automation (installing packages) to build and test pipelines. Like polish, these topics are about behind-the-scenes changes that improve the development side of Babel, but with respect to non-external errors in Babel, over aesthetic and ideal practices.

## 6.0 Pull Request

The Pull Request link can be found here: https://github.com/babel/babel/pull/10817

One of Babel’s top contributors, Nicolo-ribaudo, made a feature request, which desired four changes to Babel. The four aspects that were wanted with this feature request were:  

1. Remove all the this.hasPlugin and this.expectPlugin checks related to this plugin in packages/babel-parser/src  
2. Remove all the usages of optionalChaining in @babel/parser's tests  
3. Probably there is a test to ensure that the plugin is required; it can be removed.  
4. Move the tests from the experimental folder to es2020
	
In the pull request we made, we solved this request in its entirety. The pull request was **accepted** and will be integrated into Babel’s code base in the next minor release.

## 7.0 Conclusion

Babel is a JavaScript transpiler, that converts JavaScript to older versions to allow for backwards compatibility. Babel’s main business goals are to provide accurate transformations of JavaScript, reliably compile all versions of JavaScript to run on all browsers, and to ensure Babel is as error free as possible for each version release. Our team looked at the architecturally significant pieces of Babel, and then determined Babel’s quality attributes. We focused on maintainability and performance to create our primary presentations. Through further investigation we were able to understand the main core modules of Babel, and how they interacted with each other. This investigation gave us a deeper understanding of Babel’s architecture, and the reasoning of why it was designed this particular way, as well as any technical debt that may have been introduced as a result.

## 8.0 References

[1] 	Babel. (2019) *What is Babel?* [Online]. Available: https://babeljs.io/docs/en/

[2] 	Wikipedia. (2019) *ReDoS - Wikipedia* [Online]. Available: https://en.wikipedia.org/wiki/ReDoS

[3] 	ACM. (2019) *Code of Ethics* [Online]. Available: https://www.acm.org/code-of-ethics

[4] 	Open Collective. (2019) *Babel - Open Collective* [Online]. Available: https://opencollective.com/babel

[5] 	GitHub. (2019) *babel/babel* [Online]. Available: https://github.com/babel/babel

[6] 	Babel. (2019) *BABEL* [Online]. Available: https://babeljs.io

[7] 	GitHub. (2019) *Dependency Graph* [Online]. Available: https://github.com/babel/babel/network/dependencies

[8]	Babel. (2019) *Usage* [Online]. Available: https://babeljs.io/docs/en/usage

[9] 	Babel. (2019) *Plugins* [Online]. Available: https://babeljs.io/docs/en/plugins

[10] 	GitHub. (2019) *Issues* [Online]. Available: https://github.com/babel/babel/issues

[11] 	GitHub. (2019) *Contributing* [Online]. Available: https://github.com/babel/babel/blob/master/CONTRIBUTING.md

[12] 	GitHub. (2019) *Project* [Online]. Available: https://github.com/SENG480/course/blob/master/project.md

[13] 	GitHub. (2019) *Project-Rubric* [Online]. Available: https://github.com/SENG480/course/blob/master/project-rubric.md
