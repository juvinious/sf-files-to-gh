# sf-files-to-gh
Migrate sourceforge.net file releases to a GitHub repository as releases.

# Requirements
  - Ruby
  - Bundler
 
# Usage
It's recommended you do an initial run to create the initial configuration file. See below for configuration options.
## Standalone
```bash
$ bundle install --path vendor/bundle
$ bundle exec ruby sf-files-to-github-releases.rb
```
## Or run with shell script
```bash
$ ./run.sh
```
# Configuration
```Javascript
{
  "files": "https://sourceforge.net/projects/{project_name}/rss?path=/",
  "manifest": "./config/manifest.json",
  "release_manifest": "./config/releases.json",
  "file_manifest": "./config/files.json",
  "api": "https://api.github.com",
  "accept": "application/vnd.github.v3+json",
  "oauth_token": "",
  "user": "{github-username}",
  "repo": "{github-repository}"
}
```
| Option           | Definition                                                                         |
| ---------------- |------------------------------------------------------------------------------------|
| files            | RSS location of project files on http://sourceforge.net                            |
| manifest         | Output file used for downloading files                                             |
| release_manifest | Output file of extracted releases from manifest file                               |
| file_manifest    | Output file of file locations and information for migration                        |
| api              | GitHub API URL                                                                     |
| accept           | Set version of the GitHub API                                                      |
| oauth_token      | Github token (Generate personal tokens here: https://github.com/settings/tokens)   |
| user             | GitHub username                                                                    |
| repo             | GitHub repository in which to create releases and upload files                     |
    
# Output
```
Usage: sf-files-to-github-releases.rb [-h] [-c] [-f [file.json]] [-r] [-u]

-h, --help                   Show this help
-f, --fetch                  Fetch files from provided manifest or manifest.json
-c, --create-manifest        Create manifest only
-r, --create-releases        Create releases from manifest on github
-u, --upload-releases        Upload releases from release manifest on github
```
 
