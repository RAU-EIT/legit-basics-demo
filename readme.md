# Content Starter Pack README

If you are reading this in a repository that you have cloned from the content-starter-pack template, then you can delete this README file after you've read it and no longer need it.

The content-starter-pack repository is a starting point for new content created it LeGIT. It has sample material and the basic structure of a set of outcomes that would make up one or more courses or e-learning modules. 

There are several directories at the root of this repository that are explained in the next sections:

* ./courses
* ./outcomes
* ./output
* ./samples
* ./style-rau-base

## The ``courses`` directory

This directory is where you will develop any material for a course that is not directly part of a single outcome. Usually, this will be things like:

* assessments (test / practical) for an entire course
* course level introduction / overview presentations
* cover sheets for printed manuals that have a course title / course code displayed
* metadata for content that with audience, hardware / software versions, or other variables defined 

The ``courses`` directory already has content for a fictitious **LGT001** course; add a subfolder for each course you plan to create. 

There is also a ``courses/LGT001/builds`` directory where sample ``build.yaml`` files are configured to build the **LGT001** training content. To run one of these builds, right click on the file in the explorer pane and click **Build standalone <custom> build.yaml file**. The ``all.build.yaml`` file also demonstrates **linked builds**, referring to other build files to be built as well. 

*When you feel like you don't need the example material anymore (you've completed your development), the ``LGT001`` course folder can be deleted.*

## The ``outcomes`` directory

This directory is where you will develop all of the training content needed for each outcome. Each individual outcome (as defined in the learning design process) should be a folder within the ``outcomes`` directory. Outcomes will have content for each of the objectives and activities that outcome depends on. 

There are multiple sample outcome folders already created for use with the fictitious **LGT001** course as a reference. 

*When you feel like you don't need the example material anymore (you've completed your development), the ``outcome_##`` folders can be deleted.*

## The output directory

This directory will not be created until you do a build based on the configuration within a build yaml. Files that are 'built' go to the output directory. The output directory is ignored for git commits in order to save space. Content that you build **will not** be saved in GitHub (but the source markdown files will). 

## The ``samples`` directory

The samples directory provides resources for SMEs developing new content in LeGIT. Use them as a reference; feel free to copy content from these folders into your course / outcome specific folders at the root of your repository. There is also a full example course covering the topic 'regular expressions' included in the samples directory as a demonstration of how to write and assemble courses in LeGIT. 

Later on, when you have built some of your own material, you can remove the ``samples/courses`` and ``samples/outcomes`` directories from your repository. It is not intended to be part of your work. We recommend leaving the ``samples/_template-files`` directory in your repo, as there are files like the print user info, comments and front / back cover that you will probably use in your actual course content. If you want to delete the entire ``samples`` directory, make sure to copy images or markdown sample files you use into your own course directory and change any references to images, etc in your markdown and build files.

In the ``samples`` directory, you can find three subdirectories:

- _template-files
- outcomes
- courses

These directories all have different reference material, but are all useful to demonstrate how to write markdown and configure document builds within LeGIT.

### The ``samples/_template-files`` directory

The ___template-files__ directory contains reference markdown files for the formats that LeGIT can publish. These reference markdown files are grouped in folders by their output format, e.g. **print** for lab manuals, **presentation** for lectures and **e-learning** for, you guessed it, E-Learning. 

Each of these markdown files may refer to images that are in the ``media`` folder in the same directory. If you copy any files from here and want to use the images that were referenced in the markdown, you'll need to copy the images out of the media folder as well.

There is also a ``builds`` subdirectory which includes many sample build files for content of different formats and audiences. Use these as a reference for how to write build files for your own content. You should be able to right click on these files and 'build' output content to the output folder. 

*We don't recommend deleting this folder unless you have made sure to correctly migrate any referenced template files and their linked media somewhere else in your repository; especially for markdown content like the ``comments.md``, ``backcover.md`` and ``user-info.md`` files*

### The ``samples/outcomes`` directory

The __outcomes__ directory contains all of the markdown and media files that teach a single outcome.

In the new (circa 2026) RAU content development model, we develop content with the following hierarchy: Skill > Outcome > Objective > Activity. Skills are made up of one or more outcomes, outcomes are made of one or more objectives, etc. From a hierarchy standpoint, outcomes are the smallest unit of training a learner would consume; though it is made up of smaller pieces, we do not publish objectives or activities on their own outside of the outcome that 'wraps them up'. An outcome should be able to exist on its own, i.e. be presented by itself (for example as a single E-Learning module) and convey a meaningful outcome for the learner. 

Skills, outcomes, objectives and activities are solely learning design concepts; they do not translate directly to 'published' RAU content. Training offerings are made up of courses (for ILT and VILT) or E-Learning modules. Offerings can contain zero or more complete skills, e.g. an e-learning module could have all of the outcomes necessary to convey a skill, or multiple skills worth of outcomes, or only one outcome. Similarly, ILT courses could contain zero or more skills (through the outcomes within those skills). If this is confusing, reach out to Aba for clarification. 

When developing outcomes, it's important to develop all of the pieces of content that you need for that outcome. At a minimum there should be an interactive, passive and validation activity for each outcome, usually in the form of a presentation (passive activity), lab (interactive activity) and quiz / practical demonstration (validation activity).

*When you feel like you don't need the example material anymore (you've completed your development), this folder can be deleted.*

### The ``samples/courses`` directory

The __courses__ directory contains course specific content outside of the individual outcomes that make up a course. This usually is something like a cover page for a lab manual, or specific material that is exclusive to a single course like a setup guide or boardwork that spans multiple outcomes.

*When you feel like you don't need the example material anymore (you've completed your development), this folder can be deleted.*

## The style-rau-base directory

This directory contains the standard styles that RAU uses to make the content we create look presentable. When you first clone this repository, this directory will be empty. Make sure that you  [clone the latest style submodule](https://github.com/RAU-EIT/rau-start-here/blob/main/docs/user-guide/dry-run.md#clone-the-current-document-styles) to pull all the necessary style files. 

*This directory and all files inside should not be deleted or modified.*

