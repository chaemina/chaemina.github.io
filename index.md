---
layout: default
title: Home
nav_order: 1
description: "Just the Docs is a responsive Jekyll theme with built-in search that is easily customizable and hosted on GitHub Pages."
permalink: /
---

# Today Mina Learned <img src="./assets/images/profile-image.png" width="100" height="100">

{: .fs-9 }

개발 공부, 프로젝트 과정을 기록하는 기술 블로그 입니다.
{: .fs-6 .fw-300 }

[Categories](#getting-started){: .btn .btn-primary .fs-5 .mb-4 .mb-md-0 .mr-2 }
[View it on Github](https://github.com/chaemina){: .btn .fs-5 .mb-4 .mb-md-0 }

---

## About ME

> Chonnam National University Software Engineering Front-End Developer

| 항목                      | 기술                                               |
| :------------------------ | :------------------------------------------------- |
| **라이브러리/프레임워크** | `React` `Next.js`                                  |
| **빌드 도구**             | `CRA(Create React App)` `Vite`                     |
| **라우팅 관리**           | `React-Router`                                     |
| **HTTP 통신**             | `Axios` (Promise API 사용, JSON 자동 파싱)         |
| **상태 관리**             | `useState(Hook)` `Redux` `Jotai`                   |
| **데이터 관리**           | `Tanstack(React) Query` (자동 데이터 갱신 및 캐싱) |

React
{: .label }

Javascript
{: .label .label-yellow }

vite
{: .label .label-purple }

Next.js
{: .label .label-black }

axios
{: .label .label-purple }

npm
{: .label .label-red }

## Getting started

The [Just the Docs Template] provides the simplest, quickest, and easiest way to create a new website that uses the Just the Docs theme. To get started with creating a site, just click "[use the template]"!

{: .note }
To use the theme, you do **_not_** need to clone or fork the [Just the Docs repo]! You should do that only if you intend to browse the theme docs locally, contribute to the development of the theme, or develop a new theme based on Just the Docs.

You can easily set the site created by the template to be published on [GitHub Pages] – the [template README] file explains how to do that, along with other details.

If [Jekyll] is installed on your computer, you can also build and preview the created site _locally_. This lets you test changes before committing them, and avoids waiting for GitHub Pages.[^2] And you will be able to deploy your local build to a different platform than GitHub Pages.

More specifically, the created site:

- uses a gem-based approach, i.e. uses a `Gemfile` and loads the `just-the-docs` gem
- uses the [GitHub Pages / Actions workflow] to build and publish the site on GitHub Pages

Other than that, you're free to customize sites that you create with the template, however you like. You can easily change the versions of `just-the-docs` and Jekyll it uses, as well as adding further plugins.

{: .note }
See the theme [README][Just the Docs README] for how to use the theme as a gem without creating a new site.

## About the project

Just the Docs is &copy; 2017-{{ "now" | date: "%Y" }} by [Patrick Marsceill](https://patrickmarsceill.com).

### License

Just the Docs is distributed by an [MIT license](https://github.com/just-the-docs/just-the-docs/tree/main/LICENSE.txt).

### Contributing

When contributing to this repository, please first discuss the change you wish to make via issue,
email, or any other method with the owners of this repository before making a change. Read more about becoming a contributor in [our GitHub repo](https://github.com/just-the-docs/just-the-docs#contributing).

#### Thank you to the contributors of Just the Docs!

<ul class="list-style-none">
{% for contributor in site.github.contributors %}
  <li class="d-inline-block mr-1">
     <a href="{{ contributor.html_url }}"><img src="{{ contributor.avatar_url }}" width="32" height="32" alt="{{ contributor.login }}"></a>
  </li>
{% endfor %}
</ul>

### Code of Conduct

Just the Docs is committed to fostering a welcoming community.

[View our Code of Conduct](https://github.com/just-the-docs/just-the-docs/tree/main/CODE_OF_CONDUCT.md) on our GitHub repository.

---

[^1]: The [source file for this page] uses all three markup languages.
[^2]: [It can take up to 10 minutes for changes to your site to publish after you push the changes to GitHub](https://docs.github.com/en/pages/setting-up-a-github-pages-site-with-jekyll/creating-a-github-pages-site-with-jekyll#creating-your-site).

[Jekyll]: https://jekyllrb.com
[Markdown]: https://daringfireball.net/projects/markdown/
[Liquid]: https://github.com/Shopify/liquid/wiki
[Front matter]: https://jekyllrb.com/docs/front-matter/
[Jekyll configuration]: https://jekyllrb.com/docs/configuration/
[source file for this page]: https://github.com/just-the-docs/just-the-docs/blob/main/index.md
[Just the Docs Template]: https://just-the-docs.github.io/just-the-docs-template/
[Just the Docs]: https://just-the-docs.com
[Just the Docs repo]: https://github.com/just-the-docs/just-the-docs
[Just the Docs README]: https://github.com/just-the-docs/just-the-docs/blob/main/README.md
[GitHub Pages]: https://pages.github.com/
[Template README]: https://github.com/just-the-docs/just-the-docs-template/blob/main/README.md
[GitHub Pages / Actions workflow]: https://github.blog/changelog/2022-07-27-github-pages-custom-github-actions-workflows-beta/

[customize]: {% link docs/customization.md %}
[use the template]: https://github.com/just-the-docs/just-the-docs-template/generate
