# kuberoot-site

Static website for [KubeRoot](https://github.com/bhatnagar-afk-dev/kuberoot), served with GitHub Pages at <https://kuberoot.in>.

It does two things:

- `index.html` is the project landing page.
- `kuberoot/index.html` serves the Go vanity import path `kuberoot.in/kuberoot`, so `go get kuberoot.in/kuberoot` resolves to the GitHub repository via its `go-import` and `go-source` meta tags.

Plain HTML and CSS, no build step. `CNAME` sets the custom domain and `.nojekyll` makes Pages serve the files as-is.

## Preview locally

```sh
python3 -m http.server 8000
# open http://localhost:8000/
curl -s 'http://localhost:8000/kuberoot/?go-get=1' | grep go-import
```

## Keep the go-import tag in sync

The `go-import` meta tag in `kuberoot/index.html` must match the module path declared in the main repo's `go.mod` (`kuberoot.in/kuberoot` once the module is renamed) and point at the correct repository. If the module path or repo location changes, update this file in the same change. Each additional import path (for example a new module) needs its own page with a matching tag.

## Licence

[Apache-2.0](LICENSE)
