Host vue app on GitHub pages
=================================

1. Create a vue.config.js file in root. inside the file:

.. code-block:: js
    :linenos:

    module.exports = {
        publicPath:"/Recruitment-vue-typescript/"  // your GitHub repository name
        outputDir: "build",
    }

See the origin file, (click this :download:`link <./example/vue.config.js>` to download a copy of this file)

.. literalinclude:: ./example/vue.config.js
    :language: js
    :linenos:


Upload to GitHub and Host

.. code-block:: bash
    :linenos:

    npm run build
    git add .
    git commit -m "host on github pages"
    git push origin main
    git subtree push --prefix=build origin gh-pages
