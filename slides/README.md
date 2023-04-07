# slides

Here are some slides. They use [reveal.js](https://revealjs.com/).

You can browse them as regular markdown if you just want to see the content.

To present them as slide slides, you'll need to do a little bit of work:

1. In a location of your choice, install reveal.js using
   the [Full Setup](https://revealjs.com/installation/#full-setup) instructions,
   stopping just short of starting the server with `npm start` (or do that,
   check it works, and ctrl-C to quit).
2. In another location of your choice, check out this repository.
3. In the root of your reveal.js repository, create a symlink to this
   repository, using `ln -s $PATH_TO_PETE_DOCS .`. Check this worked
   with `ls pete-docs/slides`.
4. Start the server as directed in the reveal.js instructions.
5. Go to http://localhost:8000/pete-docs/slides/.
6. Click the slides you want to see, e.g. `demo`.
7. Navigate using the left and right keys. The `demo` slides list some more
   keyboard shortcuts.
