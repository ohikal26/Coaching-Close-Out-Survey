# PCC Coaching Close-Out

A single web page that a coaching client fills in at the end of an engagement. It turns six
short answers into a one-page PDF that the client takes into the final meeting with their
sponsor and presents themselves.

Live at: **https://ohikal26.github.io/PCC-Coaching-Close-Out/**

---

## What it does

The client answers six questions:

1. Where I started
2. What I actually worked on
3. One thing I did differently
4. What the people around me would notice
5. What I'm still working on
6. What I'd like from you

They press **Preview the page**, then **Save as PDF**. That is the whole thing.

The output is deliberately plain. No logo, no PCC branding, no coach's name. It reads as
the client's own document because that is what it is.

---

## How to publish it

Do this once. It is the same route as the two pre-coaching surveys.

1. Go to github.com and sign in.
2. Click **+** at the top right, then **New repository**.
3. Name it exactly `PCC-Coaching-Close-Out`. Set it to **Public**. Do not tick
   "Add a README file". Click **Create repository**.
4. On the next screen click **uploading an existing file**.
5. Drag in `index.html`, `README.md` and `.nojekyll`. Click **Commit changes**.
6. Go to **Settings**, then **Pages** in the left sidebar.
7. Under "Build and deployment", set Source to **Deploy from a branch**, branch to
   **main**, folder to **/ (root)**. Click **Save**.
8. Wait a minute or two, then open https://ohikal26.github.io/PCC-Coaching-Close-Out/

If the page does not appear straight away, give it five minutes and refresh. First
publishes are slower than updates.

### Updating it later

Open the repo, click `index.html`, click the pencil icon, make the change, and commit.
The live page updates within a minute.

---

## How to use it with a client

Send the link a week before the final meeting with the sponsor, with a short note. Something
like:

> Before we meet with [sponsor], have a look at this. Six questions, and the page builds a
> one-page summary you can take into the room. It is yours, not mine, so put in what you
> want them to hear and leave out what you don't.

Then do not ask to see it. The whole point is that the client owns it.

In the meeting, the client presents the page. You say very little.

---

## How to change a question

Each question is one block in `index.html` and everything about it lives in that block.
This one, for example:

```html
<div class="block" data-q="q1" data-heading="Where I started">
  <h2>1. Where I started</h2>
  <p class="prompt">What did you want to work on when this began?</p>
  <textarea id="q1" maxlength="280" data-max="280"></textarea>
  <div class="count"></div>
</div>
```

- `data-heading` is the heading that prints on the PDF.
- `<h2>` is the heading the client sees on screen.
- `<p class="prompt">` is the explanation under it.
- `maxlength` and `data-max` are the character limit. **Change both or the counter will
  lie.**

To add a seventh question, copy a whole block, change `data-q` and the `id` to `q7`, and
write the new wording. The page picks it up on its own. Keep an eye on the total: the
limits across all questions are what guarantee one page, so if you add a question, take
some characters off another.

---

## Notes

**Nothing is sent anywhere.** There is no server, no form handler, no analytics, no
tracking. The answers sit in the client's own browser using local storage so they can close
the tab and come back. The coach never sees them unless the client shares the PDF.

**One page is guaranteed by the character limits.** Tested with every field at its maximum
length and it still fits A4 with room to spare. If you raise a limit, test it again.

**The page is set to `noindex`.** It will not turn up in search results. It is not secret,
but there is no reason for it to be public-facing content.

**Browser support.** Chrome, Edge and Safari all print it correctly. In the print dialogue
the client should choose "Save as PDF" as the destination and leave margins on default.

---

## What is not in this repo

The worked example PDF built from a real client's answers. That stays out of a public
repository.
