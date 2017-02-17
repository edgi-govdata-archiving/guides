# Guides

A place to coordinate the creation of guides to identify & document best practices we can implement now to make our work future-proof.

Topics these guides will cover include:

- How data sources (i.e., federal agencies) can make stuff easier to back up
- How to produce the hash for a dataset
- How to publish a copy of a dataset
- How to represent associations between datasets that have been downloaded

This motivation for this work came out of the Next Steps track at DataRescueNYC on Feb 3-4, you can read [a report](https://hackmd.io/MYEwRgHAhloLQHYDMAWAZnFKCs24E4kBGEOCAU3AiWCLDSQDYg==?view) of the conversation

## Contributing

We need help! The process for contributing to these guides is covered in our [contributor guidelines](./CONTRIBUTING.md).

## Development

These guides are served using Github Pages and built with Jekyll. Requirements for Jekyll include Ruby, RubyGems, GCC and Make. You can follow the [Jekyll installation instructions](https://jekyllrb.com/docs/installation/).

    ```sh
    $ gem install jekyll bundler
    ```

To develop and make changes to the website clone this repo and checkout the `gh-pages` branch:

    ```sh
    $ git clone git@github.com:edgi-govdata-archiving/guides.git
    $ git checkout gh-pages
    ```

Once you have changes to test:

    ```sh
    $ bundle exec jekyll serve
    ```
