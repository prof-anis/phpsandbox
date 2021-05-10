# **PHPSandbox CI**

## What is PHPSandbox CI ?

PHPSandbox CI is a GitHub app that allows open source maintainers to manage issues and contributions to their code base by providing an environment where issues can easily be reproduced and tested without the hassles of differences in development environments! 

## WHY DO I WANT THIS ?

You must have come across bugs that are completely due to users development environment or other third party factors. Such bugs could be really difficult to reproduce talk less of fixing.  PHPSandbox CI solves this by allowing issues to first be reproduced in a notebook before a user goes on to create an issue on GitHub. Testing if a Pull Request fixes the issue is also as simple as opening notebooks generated for the Pull Request and running it content. You also have to worry less on compatibility of libraries used in the Pull request as the CI process would fail if the composer dependencies are not compatible. 

## HOW DOES IT WORK ?

A typical workflow can look like this, 
1. Someone opens an issue for a bug with a notebook url that reproduces the bug. 
2. Someone opens a pull request that fixes the issue .
3. We fork the notebook in the issue, build the library from the pull request and and install it in the forked notebook. This way, you would only have to open the created notebook to see if the changes work.  The forked notebook containing the library built from the Pull request can be used to test  if the pull request fixes the issue. 

## HOW DO I SET IT UP ?

All you need to get started is to install the GitHub app in your repository. You can then go ahead to create a ci.json file in a folder called .phpsandbox (.phpsandbox/ci.json) at the root of your project. The ci.json contains the configuration that would be used for the repository. A sample configuration is show below . You can also generate a sample configuration file [here](phpsandbox.io)

    {
	    /** 
		    The default notebooks for the repository which would be forked for every Pull Request. 
		    It is a required configuration and should contain an array of valid notebook ID's. The notebooks should also have the library installed.  
	    **/
		"notebooks": ["cpfu2", "lqsqd"],
		/** 
			The PHP version that should be used for the CI process.  
		**/
		"php": "8.0.0"
	
	}
AVAILABLE CONFIGURATION OPTIONS 
1. Notebooks
	The notebooks option should contains an array of valid notebook ID's that would be used in the build process for each Pull request. The notebooks could contain code snippets that are always tested for each pull request hence notebooks generated from them would contain the same content which can then be run to ensure that everything still works. 
2. PHP 
	This option is a string which contains the PHP version that should be used when generating notebooks 
 

## Adding more commit to a PR ? We have got you covered!

 When running the CI process, we check for notebook urls in an issue linked to the Pull request (using github linking keywords) as well as the ones in the Pull Request description. If any is found, it would be included in the build process alongside the default notebooks specified in the repository. For each commit made to a Pull Request, new notebooks would be  generated  which  contains the new changes made in the commit.  
<!--stackedit_data:
eyJoaXN0b3J5IjpbMTU4NjcwOTM2NV19
-->