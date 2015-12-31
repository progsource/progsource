# PHP Unconference 2013

The [PHP Unconference](http://www.php-unconference.de/) is a PHP conference in Hamburg. It took place this year on 21. and 22. September. Its concept is that every participant can make a talk.

At the beginning of the conference topics are presented by their speakers. Then you can vote, which topics you want to hear. After everybody has voted, a timetable is made and then you can choose four times between four topics, to which you want to go to.

Alongside to the two conference days there was a party before and the day between. Because I did not attend the parties, I cannot say much about them.

This year at day one I attended to:

1. Avoiding Burnout by David Manners
2. Code Reviews by Frank Sons
3. Log Everything by Mike Lohmann and Stefan Schadwinkel
4. Pair programming by Sebabstian Schürmann and Sönke Ruempler

At day two I went to:

1. NSA AntiPatterns / OWASP Top 10 by Tobias Zander
2. Professional English writing by Susanne Ebrecht
3. Feature Branches do not work by Kore Nordmann and Christian Otto
4. Software Migration by Sönke Ruempler

## Day 1 Review

David Manners gave some tips to **avoid burnout**. Part of it was making some workout, making breaks, make a difference between work and home, make real holidays (so don't just hang around at home - go on a journey) and make a technique free day (no computer, no phone). He said that it also helps, if you talk with someone about getting close to burnout. Take a good friend and talk with him about it. Maybe that friend can help you then with it.

Frank Sons showed ways of **Code Reviews**. There are mainly two types of code reviews. First those ones which can be in you task workflow, second Code Review meetings in which the whole team looks over critical code. The question, how to make your workmates to do Code Reviews can be answered with:

* It helps with writing Clean Code
* It saves money, because you can find bugs this way faster and earlier
* It makes you better in coding, because someone else has perhaps an idea to write some stuff shorter and so on

**Log everything** was really close to [Facebook's Wormhole](https://www.facebook.com/notes/facebook-engineering/wormhole-pubsub-system-moving-data-through-space-and-time/10151504075843920). In short: they described, how they handle their logging based on RabbitMQ, Hadoop, Hive and Erlang (for consumers) at Poker Strategy. They also wrote a book about it: [Log Everything](http://www.amazon.de/Log-Everything-ebook/dp/B00EO1AGZA/).

The **Pair Programming** talk was a good how to and why you should make pair programming. They showed how they set up their workstations at Jimdo, so that everybody can make easily pair programming. Every workstation has two monitors and two keyboards (and two chairs). It is important that the tables are big enough that two people can sit in front of them. The talk is mostly covered in [Pair Programming Illuminated by Laurie Williams and Robert Kessler](http://www.amazon.de/Pair-Programming-Illuminated-Laurie-Williams/dp/0201745763/).

## Day 2 Review

**NSA AntiPatterns / OWASP Top 10** was a walkthroug the OWASP Top 10 with examples of how to avoid security risks. To get more information of this topic, look at [OWASP](http://owasp.org/) and make sure that your libraries are up to date via [versioneye](http://versioneye.com/).

Susanne Ebrecht talked about **Professional English** and showed mainly the 5 paragraph essay and some tools to hit a minimum quality of text. Tools were for example:

* [Visual Thesaurus](http://www.visualthesaurus.com/)
* [Oxford Collocation Dictionary Online for Advanced English Learners](http://ozdic.com/)
* [Academic Word List Highlighter](http://nottingham.ac.uk/alzsh3/acvocab/awlhighlighter.html)
* [Frequency Analysis](http://www.usingenglish.com/resources/text-statistics.php)
* [Flesh readability ease](http://www.online-utility.org/english/readability_test_and_improve.jsp)

The discussion of **Feature Branches do not work** showed that it depends on the type of project if feature branches can work for you. It also showed up some possible workflow issues you can have while working with a VCS.

Sönke Ruempler showed in his talk **Software Migration** how they migrated a file server system from an old to a refactored system. In short they used feautre flags and a proxy that told the system if the old or new code should be used. Furthermore they used the deploy one-some-many pattern to test it first on one node, then one some more and at the end on all nodes.

## Conclusion

This was my second PHP Unconference. There were topics I whished I could have also attended to like Composer Plugins, but I got already some stuff that I want to look deeper into from the talks I went to. The food was okay, but perhaps a little bit too less. Espescially on the first day I heard that some poeple did not get anything to eat. At the end it was a good idea to go to the conference and if I have the time next year, I will probably go there again.

You can find some slides on the [PHP Unconference Github Wiki](https://github.com/bootev/php_unconference/wiki).
