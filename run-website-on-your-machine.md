# Run the Website on Your Machine

Our website project is stored in the following Mercurial repo: https://hg/mobile_website

1. Download and install TortoiseHg GUI from https://tortoisehg.bitbucket.io/            
This is a GUI client for Mercurial repos. Other GUI clients exist, but we recommend sticking with TortoiseHg because the entire DevExtreme team uses it.

1. Clone the website repo       
Select File -> Clone Repository. In the appeared window, do the following:

    - Specify the https://hg/mobile_website as Source and a folder on your machine as Destination.
    - Expand Options and check Do not verify host certificate to prevent the SSL:CERTIFICATE_VERIFY_FAILED error.
    - Click Clone and wait&mdash;this process takes a while.

run-website-on-your-machine-clone-window.jpg

1. Update security settings         
Open the Security window, query a host fingerprint, and enter your CORP username and password, as shown on the image below:

run-website-on-your-machine-security-window.jpg

1. Fork the documentation repo          
Go to https://github.com/DevExpress/devextreme-documentation and click Fork in the upper-right corner. Branches in this repo correspond to major DevExtreme releases (20_1, 20_2, 21_1, and so on).

1. Clone the documentation repo         
Go to the website folder from step 2 and run `PrepareWebSite.bat`. It will prompt you to enter your GitHub nickname. This .bat creates multiple clones of the docs repo&mdash;one for every major DevExtreme version.

Why is this needed? We maintain docs for three DevExtreme versions (previous, current, and future), each has a separate branch. Let's call them "main branches". When you edit docs, you create many other branches-descendants from the main branches. With so many branches at hand, it's easy to confuse which branch descents from which. Multiple clones make sure that this doesn't happen as you always work with a specific branch and its descendants in a separate clone. With multiple clones, it's also easy to run multiple docs versions on the website simultaneously.

1. Download and install a GUI to work with Git      
The DevExtreme team mostly uses SourceTree - https://www.sourcetreeapp.com/ If you are a devoted user of the command line, install SourceTree anyway because your collagues might need it when you will work on some document together.

1. Open tabs 

    Open the SourceTree, press Ctrl + O, and specify a folder with a cloned docs version. For example, %path_to_the_site%\Docs\Source\19_2. This is where you will be working with version 19.2. Repeat this step for all the needed versions (currently, 20.1). 