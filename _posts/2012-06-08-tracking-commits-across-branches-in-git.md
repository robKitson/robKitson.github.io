---
layout: post
title:  "Tracking Commits Across Branches in Git"
date:   2012-06-08 00:00:00 -0800
categories: 
---
Recently I had to give a few colleagues a tutorial on how to figure out which branches a particular commit has been applied to in a Git repository. Not hard-core git by any means, but useful nonetheless.

##Local Repos

If you want to see which branches in your local repo contain a commit use this command:

{% highlight bash %}
git branch --contains <commit SHA>
{% endhighlight %}

The results, if there are any, should be a list of local branches :

    env_stage
    feature_branch1
    feature_branch1-TO-master
    feature_branch1-TO-other_branch
    other_feature_branch

In the example above the commit I'm looking for was a part of the work done on "feature_branch1", which has been merged to other_branch and master using merge branches. Since the changes were pulled into master (and I'm constantly pulling master to get the latest changes) the next time I branched from master to work on a new feature (other_feature_branch) the commits from feature_branch1 were included.

##Remote Repos

If you want to see which branches on your remote repo(s) contain a commit simply add the -r switch to the command:

{% highlight bash %}
git branch -r --contains <commit SHA>
{% endhighlight %}

The results, if there are any, will be a list of fully-qualified branch names:

    origin/master
    origin/feature_branch1
    origin/feature_branch1-TO-master
    origin/feature_branch1-TO-other_branch
    origin/acid_burn
    origin/crash_override
    origin/zero_cool

In this case it appears that the work that was done on featurebranch1 and has been pull-requested to stage, and 3 new branches have been started since: acid_burn, crash_override, and zero_cool. It would be awesome if the engineer responsible for feature_branch1-TO-env_stage and feature_branch1-TO-other_branch would delete those merge branches since we still have the feature branch, and the changes have been merged to master. feature_branch1 should not be deleted until that feature ships.