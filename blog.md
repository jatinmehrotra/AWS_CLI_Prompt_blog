<blockquote>
AWS and its ecosystem of service is HUGE and ever-growing, keeping track of each service and its usage is easy/manageable when it comes to AWS Console, but it takes a toll on users to use the same/new services on `aws-cli` especially remembering the nitty gritty of each service's command line usage.


This article talks about one of the most anticipated and awaited features which was announced in the release of AWS CLI version 2 (v2) on 10 Feb,2020

</blockquote>

## What is AWS CLI Auto Prompt Feature?

AWS CLI v2 was based on a theme which wanted to help users by adding bunch of interactive features. Version 2 automatically prompt us commands, parameters and resources whenever we run an `aws command`.
It cannot get better as to how *simple, easy and intuitive* it makes for a user by serving everything on this auto-prompt platter.

![introduction](https://cdn-ssl-devio-img.classmethod.jp/wp-content/uploads/2021/07/Screenshot_2021-07-07_at_11_48_39_PM-compressed-scaled.jpg)

### Prerequisite

- Auto feature is only available in **AWS CLI version 2**. To update [check the docs](https://docs.aws.amazon.com/cli/latest/userguide/install-cliv2.html).



- [sourcecode language="bash"]
  
   aws --version  #to check your cli version
  
  [/sourcecode]

## How to configure Auto-Prompt?

- Auto Prompt has 2 modes which can be configured by 3 ways.
  
  - **Default enable/disable**: Users can configure, to permanently enable/disable auto-prompt feature by saving this particular setting in their config file under default profile.
  
      Example for config file.

      [sourcecode language="text"]

      [profile default]
      region = ap-northeast-1
      output = json
      role_arn = arn:aws:iam::xxxxxxx:role/cm-xxxxx.xxxx
      mfa_serial = arn:aws:iam::xxxxxxx:mfa/cm-xxxxxx.xxxxx
      cli_auto_prompt = on
      source_profile = gateway

      [/sourcecode]
       
       
 - **Environment variable**: Note this overides any value loaded from config file
  

     [sourcecode language="bash"]

     export aws_cli_auto_prompt=on

     [/sourcecode]


 - **one time use**: Note this overrides any value from config file and environment variable.For a single command either enable or disable auto-prompt by specifying <strong>command line option.</strong>

  
  
     [sourcecode language="bash"]
  
     aws s3 ls --cli-auto-prompt  # to enable
     aws dynamodb describe-table --table-name trialTable --no-cli-auto-prompt # to disable 
   
  
     [/sourcecode]

- There are 2 modes of auto-prompt one is full which gives **full functionality**, another is **partial** which is for few commands or particularly use case would be pre-existing scripts or runbooks.

## How It is used?

- Whenever users start typing commands partially (even a single letter), auto-prompt automatically suggest based on what we type.
- Suggestions can range from the name of `commands, parameters, resources` and their options and descriptions.
- To select a suggestion all we need is to `use arrow keys and hit the ENTER key`.  

## The scope and powers of auto-prompt

This articles uses default method to enable aws. To start ```aws in auto prompt just type aws in terminal```. 

- **To show Documentation**
   
   Auto prompt will automatically show `documentation` on the fly as commands and their options changes. To toggle documentation **on/off use F3** ( either in the beginning or any point in time).
 
 ![documentation](https://cdn-ssl-devio-img.classmethod.jp/wp-content/uploads/2021/07/Screenshot-2021-07-07-at-11.56.44-PM-scaled.jpg)  
  
 ![documentation-2](https://cdn-ssl-devio-img.classmethod.jp/wp-content/uploads/2021/07/Screenshot-2021-07-07-at-11.56.55-PM-scaled.jpg)
  

- **Completing commands automatically**

   auto-prompt `searches and suggest all the possible commands` which matches with a particular letter.
   
   - All commands starting with d
   
   ![d-commands](https://cdn-ssl-devio-img.classmethod.jp/wp-content/uploads/2021/07/Screenshot-2021-07-08-at-12.02.33-AM-scaled.jpg)
   
   - All commands having `data` within them
   
    ![d-commands](https://cdn-ssl-devio-img.classmethod.jp/wp-content/uploads/2021/07/Screenshot-2021-07-08-at-12.02.33-AM-scaled.jpg)

- **Commands options, region, profile completion**

    After a command is typed, auto-prompt automatically suggest that particular commands options as well as their descriptions, not only this it automactically shows all regions for `region ` option and even `local profiles` configured for our aws cli.
    
    - commands options
    
    ![command options](https://cdn-ssl-devio-img.classmethod.jp/wp-content/uploads/2021/07/Screenshot-2021-07-08-at-12.04.49-AM-scaled.jpg)
    
    - region 
    
    ![region](https://cdn-ssl-devio-img.classmethod.jp/wp-content/uploads/2021/07/Screenshot_2021-07-08_at_12_09_01_AM-scaled.jpg)
    
    
   - profile completion
    
    ![profile-completion](https://cdn-ssl-devio-img.classmethod.jp/wp-content/uploads/2021/07/Screenshot_2021-07-08_at_12_09_20_AM-scaled.jpg)

- **Viewing history of commands**

    auto-promp allows us to see histroy of previously used commands in this mode. To see `history` hit `CTRL + R`

    ![history](https://cdn-ssl-devio-img.classmethod.jp/wp-content/uploads/2021/07/Screenshot_2021-07-08_at_12_13_51_AM-scaled.jpg)

## Sum-up

This article shows how auto-prompt makes so `easy, productive, and super fast user experience in aws cli` with the ever-growing aws services. AWS CLI and its commands is **no more a mystery for anyone**. Check this for more [features of aws cli](https://aws.amazon.com/blogs/developer/aws-cli-v2-is-now-generally-available/).

Till then, **Happy Learning!**