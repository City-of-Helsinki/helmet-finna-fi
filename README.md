# helmet-finna-fi

Versioned configuration for Helmet.fi Finna instance.

## Purpose of this repository

The purpose of this repository is to store the configuration of helmet.finna.fi so that the text-based configuration (configuration files, phtml templates, css styles etc.) can be versioned and linked in Finna and binary content (images etc.) backed up.

The main benefit of using Git for version control is that it automatically creates a change log based on the commits and also keeps a backup copy of the settings in a separate place to support disaster recovery. An additional benefit is that the configuration doesn't have to be edited via Finna's web UI thus allowing full-featured editors such as VSCode to be used instead.

The downside of using Git for version control is that Finna doesn't yet support automatic linking of external repositories to its file manager. This requires files to be linked and updated manually. Thus, it is a good idea to keep the changes small and follow the operating instructions below.

## Prerequisites

- Membership in city-of-helsinki Github organization with SSH keys enrolled 
- Git and a code editor installed to your workstation
- Access to Finna administration UI at https://hallinta.finna-pre.fi
- Commit access to this repository

## Operating instructions

This repository mirrors the path structure of a Finna View (Näkymä) so that the dirrectories and files under finna-view-root correspond to ones under one Finna view.

Clone the repository with following command

```
git clone git@github.com:City-of-Helsinki/helmet-finna-fi.git
```

Only main branch is used.

The files are manually linked using the Finna File Manager (Tiedostonhallinta).

1. First create or look up the file you want to link in Finna.
2. Note the path of the file in Finna File Manager and make sure that you recreate the same path up from the View root in this repository
3. Create a file with the same name in this repository
4. Edit the contents of the file you just created (If it's an existing file in Finna, you can copy-paste the contents from the File Manager)
5. Make sure you save the file in the editor
6. Stage the change to version control and make a commit of it by issuing commands ```git add -A && git commit -m "COMMIT_MESSAGE_HERE"``` (Note: replace the string COMMIT_MESSAGE_HERE with a description of the change you made)
7. Push the change into this repository by issuing command ```git push```
8. In case the changes were to a file that isn't already linked to a Github URL you need to make link it to its raw URL. The raw URL is ```https://raw.githubusercontent.com/City-of-Helsinki/helmet-finna-fi/main/finna-view-root/``` + the file path up to the root of the Finna View. For example, the raw URL for ```/local/config/vufind/browse.ini``` is ```https://raw.githubusercontent.com/City-of-Helsinki/helmet-finna-fi/main/finna-view-root/local/config/vufind/browse.ini```. Copy-paste this path into Finna File Manager text editor URL link bar, click "Linkitä" (link) and then "Tallenna" (save).
9. Check that the linking worked

We hope that Finna will receive support for external content repositories soon as it will make things easier.

## Caveats

Note that some VPN solutions might prevent the use of SSH which also blocks Git.