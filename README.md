Blogs | Swastik Sharma
=======
[blog.swastiksharma.me](https://blog.swastiksharma.me)

## Usage
#### Setup
```console
bundle install
```
#### Serve
```console
bundle exec jekyll serve
```
## Probable errors
`bundle install` failed due to permission denied

**Solution**

According to [bundler documentation](), a **$BUNDLE_PATH** or **$GEM_HOME** env variable can be set to make it the default writeable place.
```console
export BUNDLE_PATH=~/.gems
bundle install
```
Then run the command as usual
```console
bundle exec jekyll serve
```




