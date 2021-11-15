# How Google, Twitter, and Spotify built a culture of documentation

[toc]

> 软件公司的内部文档，往往是一个痛点，要么根本没有文档，要么就是杂乱不堪，分散在代码、Word 文件、Confluence 等各处。软件公司越大，这个问题越严重，本文介绍三家大型互联网公司如何处理内部文档。
>
> -- [阮一峰](https://www.ruanyifeng.com/blog/2021/11/weekly-issue-182.html)



Many technical problems ultimately turn out to be people problems, and a lack of good documentation is no exception. Writing and maintaining documentation is a habit that needs to be encouraged and nurtured. The unfortunate truth is that no amount of tooling is going to help without a **culture of documentation**. Today we’ll look at how 3 high performance engineering companies, Google, Twitter, and Spotify, handle their technical documentation and built a culture of documentation.

## Google

[Riona MacNamara](https://twitter.com/rionam) has a fantastic [talk from 2016](https://www.usenix.org/conference/srecon16europe/program/presentation/macnamara) talking about her work at Google improving the state of their internal documentation. We highly encourage you to watch the talk (it’s only ~30 minutes), but here are a few interesting highlights of the problems they faced back in 2014:

- **48% of Google engineers cited bad docs as #1 productivity issue**
- **50%+ of SRE issues cited problems with docs**
- Docs were considered everybody’s problem, but nobody’s job

Everyone felt the pain of bad docs. Despite numerous past efforts, nothing had worked. Documentation remained spread out in wikis, random documents, or even offline on whiteboards. Embedding technical writers into a team would help for a while, but documentation would quickly deteriorate after the writers left.

So what worked for them to start changing the status quo? **They made documentation radically simpler for their engineers** with a system called *g3docs*. It did the following:

- Remove decisions - present one way to document things
- Host docs next to the code in source in Markdown so engineers can stay in their IDE
- Docs get automatically rendered into nice HTML pages on commits

On top of the tooling work they did, the team went around creating organizational change:

- Formed alliances with influential engineers to introduce the tooling
- Partnered with specific teams to build strategic integrations
- Released and iterated in the open
- Never *forced* teams into a new workflow - lead by example

After g3docs was adopted, usage grew to 200K+ documentation updates and 3.9 million page views a month *(NOTE: these numbers are from 2016)*.

## Twitter

Back in 2014, Twitter had 3 technical doc writers. Among other things it was their responsibility to assist the 1000+ software engineers with internal documentation. At the same time, the general atmosphere around docs at Twitter was that they were incomplete, out of date, or even nonexistent. Most documentation lived in Confluence, but some were in Google Docs or READMEs.

[Simeon Franklin](https://twitter.com/simeonfranklin) and [Marko Gargenta](https://twitter.com/markog) have a [great talk](https://www.youtube.com/watch?v=6y4eQ6gYwdU) where they discuss the strategy they took. Similar to Google, they embarked on a journey to change hearts and minds about documentation.

They bring up the example of software engineers and testing: it was not long ago that software engineers were not expected to write tests. This expectation has been flipped, and today untested code is frowned upon. They wanted to do the same thing for docs internally at Twitter.

Their approach came in 3 parts:

- Encourage documentation via education and special **DocDays**
- Build a new **docs-as-code** stack (DocBird)
- Create **documentation templates**

They organized **DocDays**, which are single-day hackathons where developers update their docs. Technical writers would give training on the day, and help edit the final docs. The bigger purpose of these days was to evangelize and normalize documentation writing as a practice. It builds community and a common set of expectations about documentation.

To make documenting easier and standardized, they launched a new docs-as-code stack called DocBird, which is a customized wrapper around [Sphinx](https://www.sphinx-doc.org/en/master/). Similar to g3docs, it builds your documentation from source automatically. It removes the questions of *“where are the docs”*.

Finally, they created shared templates for documentation. These have common sections and questions and could be copied into projects to use as starting points. Staring at a blank canvas can sometimes be the hardest part of getting started writing.

## Spotify

What makes Spotify’s story interesting is that they have open sourced much of the stack they use for their documentation approach in a project called [Backstage](https://backstage.io/).

Backstage is a software catalog for Spotify’s numerous microservices. It has a long list of features and plugins, but one of the most popular features has been the [integrated docs-as-code support](https://backstage.io/blog/2020/09/08/announcing-tech-docs).

> Internally, we call it TechDocs. It’s the most used plugin at Spotify by far — accounting for about 20% of our Backstage traffic (even though it is just one of 130+ plugins).

Spotify’s journey to Backstage’s docs-as-code starts just like our previous case studies: **the 3rd largest problem according to engineers was not being able to find the technical documentation they needed to do their work.** Docs were spread across Confluence, Google Docs, custom sites, and nothing could ever be found.

[Gary Niemen](https://twitter.com/garyniemen) has a talk where he discusses their team’s work in building out Spotify’s “docs-as-code+” infrastructure. He highlights a couple interesting learnings:

- Keep the solutions simple - so it just works
- Fiercely optimize for the engineer
- Standardize and centralize

Their goal for the technical writing team is to have engineers go from “stuck to unstuck” in 1 minute with their documentation. They continue to move the needle towards this goal.

## What can we learn?

There are a lot of common themes in these stories, but the learnings can be boiled down to 3 main points:

- Make the engineer’s life as easy as possible - remove friction
- Standardize and invest in your tools
- Make documentation an expectation through teaching and leading by example

What we saw in these three cases, and many readers will likely agree based on experience, engineers will not maintain documentation in wikis. The context switch of moving from your code to a separate system and not being able to use your existing tooling means that documentation will be forgotten about. In these examples all three companies went with a [docs-as-code](https://blog.doctave.com/2021/08/30/why-you-should-consider-docs-as-code.html) approach because of how frictionless it makes updating documentation for developers.

All 3 companies also invested heavily in tooling. Whatever you choose for your documentation stack (we obviously strongly believe [Doctave](https://www.doctave.com/) is an excellent solution), stick with it and make sure that is the only place for technical documentation. There should never be a question about where the docs live.

Finally, and this is likely the hardest part, you need to make documentation a part of the engineering culture. This means teaching developers how to write docs, providing examples and templates to use, organizing hack days dedicated to documentation, and working with influential engineers in your organization to set expectations. Just like how testing became a norm accepted by most engineers today, so can documentation.



## Reference

1. [How Google, Twitter, and Spotify built a culture of documentation](https://blog.doctave.com/2021/09/07/how-google-twitter-and-spotify-build-culture-of-documentation.html)
2. [Why you should consider using docs-as-code](https://blog.doctave.com/2021/08/30/why-you-should-consider-docs-as-code.html)
3. [Spotify --An open platform for building developer portals ](https://backstage.io/)
4. [[Announcing TechDocs: Spotify’s docs-like-code plugin for Backstage](https://backstage.io/blog/2020/09/08/announcing-tech-docs)](https://backstage.io/blog/2020/09/08/announcing-tech-docs)