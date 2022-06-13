# Path to Programming Blog

## Local Build

---

To build locally you must pull in the latest ananke theme submodule.

Run the following command:

`git submodule update --init --recursive`

Now you can run the app locally without any errors by running the following command:

`hugo serve -D`

Navigate to http://localhost:1313 to see changes locally.

The Hugo CLI can be downloaded at [gohugo.io](https://gohugo.io/getting-started/installing/).

## Adding New Posts

Enter the following in your terminal:

`hugo new posts/my-post-name.md` 

## Schedule Posts using Github Actions

This blog uses the [merge-scheduler Github Action](https://www.jasongaylord.com/blog/2020/07/31/schedule-merging-pull-requests-in-github). To schedule a new article, add `/schedule 2020-08` as a comment on the PR.

## How to add links that open in new tab

{{< a_blank title="Text Goes Here" url="https://myurl.com/" >}}