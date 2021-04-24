What is React?
======================

.. image:: React.png
    :width: 400

The idea for React first came about when Facebook developers realized
they were running into issues with code maintenance. As Facebook continued to grow as
a company, they needed to hire more people to help push out more updates to keep
their app running smoothly and efficiently. On top of that, they needed something
to help improve the user interface (UI) of their website. After a while, the
engineers just couldn't keep up with everything and had to come up with a
better solution. That was the beginning of React and the beginning of one of the
best mobile app/website development programs today.

In 2011, Jordan Walke, a software engineer for Facebook, created FaxJS which was
the earliest prototype of React. Just a few short years after Jordan created FaxJS,
Facebook acquired Instagram and increased their number of users substantially.
Soon after this acquisition, Jordan Walke introduced React to the world as it became
open sourced. React did not get the reaction that most people at Facebook had
probably expected though. Many people believed that React was actually a step
backward for the company, but as people started to work with it and Jordan started
to make some small changes, people started to get on board. One of the best things
that happened to React early on was in December of 2013. During this time, David
Nolen introduced Om Next, which is a Javascript Model-View-Controller (MVC) Framework
based on React, and explained in his blogs about how much he loved using React.
The release of Om Next helped many early adopters want to start using React and
allowed a large group of people to learn more about what React was. [#f1]_

Declarative Views
-----------------

One of the greatest things with React is that is allows for declarative views. This
allows you to control flow and state in your application by saying "It should
look like this." Some of the benefits from declarative views include the ability
to update and render components much more easily as well as, makes your code much
more predictable and easier to debug. To better describe the difference in
imperative to declarative views, you can use something like how to make dinner.
In an imperative view, you would need to describe step by step how to make dinner
like:

.. code-block:: JavaScript
    :linenos:
    :caption: Imperative View

        Go to the kitchen
        Open fridge
        Remove chicken from fridge
        ...
        Bring food to the table

However, with declarative views, you can just tell the code exactly
what you want because it already knows how to make the chicken. For example, "I
want dinner with chicken" rather than explaining step by step.

.. code-block:: JavaScript
    :linenos:
    :caption: Declarative View

        I want dinner with chicken.

Based on that example you can see how it would be much easier to figure
out where a bug might be in a single line of code as opposed to multiple. This helps
with much quicker improvements to your code and allows for the initial creation
of the code to be completed much faster. [#f2]_

Components
----------

In addition to the declarative views in React, it uses components that can manage
their own state and can later be composed to make complex UIs. React components
implement a ``render()`` method that takes input data and returns what to display.
Below is an example of a React component where "Hello Taylor" would be displayed.
The input data that is being passed into the component is being accessed by
``render()`` via ``this.props.``

.. code-block:: JavaScript
    :linenos:
    :caption: Code to print Hello Taylor

        class HelloMessage extends React.Component {
          render() {
            return (
              <div>
                Hello {this.props.name}
              </div>
            );
          }
        }

        ReactDOM.render(
          <HelloMessage name="Taylor" />,
          document.getElementById('hello-example')
        );

A much more complex component that can be used in React is adding in external
plugins into your components. This allows you to interface with other libraries
and frameworks. This example uses **remarkable**, an external Markdown library, to
convert the <textarea>’s value in real time.

.. code-block:: JavaScript
    :linenos:
    :caption: Code to connect to an external library

        class MarkdownEditor extends React.Component {
          constructor(props) {
            super(props);
            this.md = new Remarkable();
            this.handleChange = this.handleChange.bind(this);
            this.state = { value: 'Hello, **world**!' };
          }

          handleChange(e) {
            this.setState({ value: e.target.value });
          }

          getRawMarkup() {
            return { __html: this.md.render(this.state.value) };
          }

          render() {
            return (
              <div className="MarkdownEditor">
                <h3>Input</h3>
                <label htmlFor="markdown-content">
                  Enter some markdown
                </label>
                <textarea
                  id="markdown-content"
                  onChange={this.handleChange}
                  defaultValue={this.state.value}
                />
                <h3>Output</h3>
                <div
                  className="content"
                  dangerouslySetInnerHTML={this.getRawMarkup()}
                />
              </div>
            );
          }
        }

        ReactDOM.render(
          <MarkdownEditor />,
          document.getElementById('markdown-example')
        );

This component would allow a user to enter text such as "Hello, **world**!" and
the component would then return Hello, **world**!

Finally, this is a variable declaration that would be used in React. The tag is
neither a string nor HTML. It is call JSX and is a syntax extension to JavaScript.
JSX produces React elements. "React embraces the fact that rendering logic is inherently
coupled with other UI logic: how events are handled, how the state changes over time,
and how the data is prepared for display." [#f3]_

.. code-block:: JavaScript
    :linenos:
    :caption: Basic Hello, world!

        const element = <h1>Hello, world!</h1>;

Where it's Used
---------------

React has become such a widespread and used tool that a number of larger companies
are now using it within their mobile apps and websites. Some of the most noteable
names are Facebook, Instagram, Khan Academy, Code Academy, The New York Times,
Netflix, and Discord. All of these companies have great reviews of React and love
how much better it makes their mobile apps and websites. It is actually very easy
to find companies that are using React through the google extension react-detector.
I tried it out and it's pretty cool when it actually works. Sometimes it does not
highlight all of the components made with React but it does show them every so
often. You can try it out for yourself by searching React-Detector extension and
adding it to you browser.

.. image:: discord-mascot.png
    :width: 180

.. image:: Facebook.png
    :width: 180

Here is a quote from Discord's Mobile Engineering Director, Miguel Gaeta on their
use of React, "Early on at Discord, we adopted React Native as soon as it was
open-sourced to build our iOS app from the core of our React app. Years later,
we are still happy with that decision. Our iOS app currently sees many millions
of monthly active users, is 99.9% crash-free, and holds a 4.8-star rating on the
app store. React Native has been instrumental in allowing us to achieve this with
a team of only three core iOS engineers!" [#f4]_ In addition to Miguel's quote, there are
hundreds of other React users who have incredibly positive reviews on the program.
Just another example comes from a small coding blog by Christoph Michael who says,
"I’ll definitely use React Native for my next app again - I can develop faster
without the need to learn the Android API and, as the community grows, there will
be more and more Native modules available." [#f5]_

Adding React to Your Own Website
----------------------------

In this section, you will learn how quickly and easily you can implement React into
your own website. We will look at how to add a "Like" button onto your website.

**1. Add a DOM Container to the HTML**

First, open the HTML page you want to edit. Add an empty ``<div>`` tag to mark
the spot where you want to display something with React. For example:

.. code-block:: html
    :linenos:
    :caption: Adding DOM container

        <!-- ... existing HTML ... -->

        <div id="like_button_container"></div>

        <!-- ... existing HTML ... -->

**2. Add the Script Tags**

Next, add three ``<script>`` tags to the HTML page right before the closing
``</body>`` tag:

.. code-block:: html
    :linenos:
    :caption: Adding script tags

    <!-- ... other HTML ... -->

    <!-- Load React. -->
    <!-- Note: when deploying, replace "development.js" with "production.min.js". -->
      <script src="https://unpkg.com/react@17/umd/react.development.js" crossorigin></script>
      <script src="https://unpkg.com/react-dom@17/umd/react-dom.development.js" crossorigin></script>

      <!-- Load the React component. -->
      <script src="like_button.js"></script>

    </body>

The first two tags load React. The third one will load your component code.

**3. Create a React Component**

Create a file called like_button.js next to your HTML page.

Use this starter code and paste it into the file you created.

.. code-block:: JavaScript
    :linenos:
    :caption: Starter Code

        'use strict';

        const e = React.createElement;

        class LikeButton extends React.Component {
          constructor(props) {
            super(props);
            this.state = { liked: false };
          }

          render() {
            if (this.state.liked) {
              return 'You liked this.';
            }

            return e(
              'button',
              { onClick: () => this.setState({ liked: true }) },
              'Like'
            );
          }
        }

After the starter code, add two lines to the bottom of like_button.js:

.. code-block:: JavaScript
    :linenos:
    :caption: Final Step

    // ... the starter code you pasted ...

    const domContainer = document.querySelector('#like_button_container');
    ReactDOM.render(e(LikeButton), domContainer);


These two lines of code find the ``<div>`` you added to your HTML in the first step,
and then display the “Like” button React component inside of it.

And that's it! After completing these simple steps, you have successfully added
React's "Like" button component into your website.

Conclusion
----------

All of these quotes and the growing population of mobile apps and websites is allowing
React to reach out to a much larger group of people as more and more people learn
about it. Over the next few years, React could become more frequently used as they
continue to develop and improve the program to continuously improve it. However,
the world of technology is ever changing and who knows what other technologies will
be available in the coming years. In the meantime, React will continue to be one
of the best options for mobile app/website development and continue to push the
boundaries of development.


.. [#f1] Hámori, Ferenc. “The History of React.js on a Timeline: @RisingStack.” RisingStack Engineering - Node.js Tutorials &amp; Resources, RisingStack Engineering - Node.js Tutorials &amp; Resources, 10 Feb. 2020, blog.risingstack.com/the-history-of-react-js-on-a-timeline/.
.. [#f2] Nathan Hagen. “Difference between Declarative and Imperative in React.js?” Stack Overflow, 1 Aug. 1964, stackoverflow.com/questions/33655534/difference-between-declarative-and-imperative-in-react-js#:~:text=A%20declarative%20style%2C%20like%20what,It%20should%20look%20like%20this%22.&amp;text=You're%20delegating%20the%20organizational,have%20to%20worry%20about%20state.
.. [#f3] React – a JavaScript library for building user interfaces. (n.d.). Retrieved February 11, 2021, from https://reactjs.org/
.. [#f4] Gaeta, Michael. “How Discord Achieves Native IOS Performance with React Native.” Medium, 7 Nov. 2019, blog.discord.com/how-discord-achieves-native-ios-performance-with-react-native-390c84dcd502.
.. [#f5] Michel, Christoph. “What I Learned from Building My First React Native App.” Cmichel Blog, 26 Oct. 2016, cmichel.io/lessons-from-building-first-react-native-app.