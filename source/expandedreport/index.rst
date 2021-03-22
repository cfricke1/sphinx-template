Early Stages of React
======================

React first came into discussion when Facebook developers realized they were running
into issues with code maintenance. As Facebook began to grow as a company and started
to gain a lot of new users, they needed to hire a lot more people and push out a
lot more updates to keep the app running smoothly. After a while however, the
engineers just couldn't keep up with everything and had to come up with a better
solution. That is where React began.

In 2011, Jordan Walke created FaxJS which was the earliest prototype of React.
Just a few short years after that in 2013, after Facebook's acquisition of Instagram
and increasing their number of users substantially, Jordan Walke introduced React
to the world as it became open sourced. React did not get the reaction that most
people at Facebook had probably expected though. Many people believed that React
was actually a step backward for the company, but as people started to work with
it and Jordan started to make some small changes, people started to get on board.
One of the best things that happened to React early on was in December of 2013,
David Nolen introduced OM which is based on React and basically explained how
awesome React is which helped many early adopters want to use it and boosted the
number of people who even knew it was a thing. [#f1]_

ReactDOM.render(
  <h1>Hello, world!</h1>,
  document.getElementById('root')
);

Here is just a basic "Hello World" that a user would use in React.

const element = <h1>Hello, world!</h1>;

In addition, this is a variable declaration that would be used in React. The tag is
neither a string nor HTML. It is call JSX and is a syntax extension to JavaScript.
JSX produces React elements. "React embraces the fact that rendering logic is inherently
coupled with other UI logic: how events are handled, how the state changes over time,
and how the data is prepared for display." [#f2]_

.. [#f1] Hámori, Ferenc. “The History of React.js on a Timeline: @RisingStack.” RisingStack Engineering - Node.js Tutorials &amp; Resources, RisingStack Engineering - Node.js Tutorials &amp; Resources, 10 Feb. 2020, blog.risingstack.com/the-history-of-react-js-on-a-timeline/.
.. [#f2] React – a JavaScript library for building user interfaces. (n.d.). Retrieved February 11, 2021, from https://reactjs.org/