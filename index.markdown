---
# Feel free to add content and custom Front Matter to this file.
# To modify the layout, see https://jekyllrb.com/docs/themes/#overriding-theme-defaults

layout: home
---

<!-- ---
layout: post
title:  "Welcome to Jekyll!"
date:   2023-11-02 18:00:23 +0100
categories: jekyll update -->


# clembench: Systematic Evaluation of Chat-Optimized Language Models as Conversational Agents

> Chalamalasetti, K., Götze, J., Hakimov, S., Madureira, B., Sadler, P., & Schlangen, D. (2023). clembench: Using Game Play to Evaluate Chat-Optimized Language Models as Conversational Agents. In Proceedings of EMNLP 2023. [PDF](https://aclanthology.org/2023.emnlp-main.689.pdf) DOI: [10.18653/v1/2023.emnlp-main.689](https://www.doi.org/10.18653/v1/2023.emnlp-main.689)


<div class='iframe-video'>
    <iframe 
        src="https://videoup.uni-potsdam.de/Panopto/Pages/Embed.aspx?id=e33235a9-32fe-4cd0-9775-b0c2009135d0&autoplay=false&offerviewer=true&showtitle=true&showbrand=false&captions=true&interactivity=all" 
        style="border: 1px solid #464646;" 
        allowfullscreen 
        allow="autoplay">
    </iframe>
</div>


There are currently two main paradigms for evaluating LLMs: *reference-based* evaluation looks at the performance at well-defined single-shot tasks like question answering or summarisation; while *preference-based* evaluation asks users to interact with such two such models (each interfaced as a potentially multi-turn chatbot) in parallel and to judge which one "performs better".

We propose **a complementary way of evaluating LLMs** which combines the control (and reproducibility that comes from automation) that reference-based evaluation offers with the interactivity challenged in chatbot-type preferential evaluation. This is achieved **through *gameplay* in well-defined conversational / dialogue games**. We have implemented a set of games (such as Wordle or Taboo, or games where one player must formulate descriptions of what to do to another player) which current models can play *in self-play*. These games come with metrics that measure the quality of the game play. Together, across the set of games, we can calculate an overal score per model (what we call the *clemscore*) which serves as an indicator of how well the model can follow fine-grained instructions and how well it can simulate goal-directed conversational behaviour.

The framework for implementing such games and for running the overall benchmark [is described in the code repo](https://github.com/clembench/clembench). The implemented games that form the current version of the *clembench* are described in the paper. Here, you can find the results of running the collection of games that forms the current version of the *clembench* against the list of models shown below. 

We plan to continuously update the leaderboard with new models; and the benchmark with additional games. (Last update: *2023-11-20*; models added.)


<!--
# CLEMs (Chat-Optimized LLMs) Evaluated

{% include_relative _posts/output_markdowns/models.md %}

The evaluated models with the details about
number of parameters in billions, trained data size
(tokens) in billions (to the extent that this is known).
-->



# Interaction Settings in the Current Version

<div class="table-container">
<table>
    <thead>
    <tr style="text-align: center;">
      <th>interaction setting</th>
      <th>description</th>
      <th>anchoring process</th>
      <th>representational domain</th>
    </tr>
  </thead>
  <tbody>
    <tr style="text-align: center;">
      <td>taboo</td>
      <td>A game where one player tries to get the other player to guess a word without using certain 'taboo' words in their clues.</td>
      <td>incremental learning/processing</td>
      <td>language model/world model</td>
    </tr>
    <tr style="text-align: center;">
      <td>wordle</td>
      <td>A game where one player thinks of a word and the other player tries to guess it by suggesting words that are similar or related.</td>
      <td>incremental learning/processing</td>
      <td>language model/world model</td>
    </tr>
    <tr style="text-align: center;">
      <td>wordle_withclue</td>
      <td>A variant of Wordle where the guesser is given a clue to help them guess the target word.</td>
      <td>incremental learning/processing</td>
      <td>language model/world model</td>
    </tr>
    <tr style="text-align: center;">
      <td>wordle_withcritic</td>
      <td>A variant of Wordle where the guesser's suggestions are evaluated by a third player, who provides feedback on their accuracy.</td>
      <td>incremental learning/processing</td>
      <td>language model/world model</td>
    </tr>
    <tr style="text-align: center;">
      <td>imagegame</td>
      <td>A game where one player draws a picture and the other player tries to guess what it represents.</td>
      <td>multimodal grounding</td>
      <td>situation model</td>
    </tr>
    <tr style="text-align: center;">
      <td>referencegame</td>
      <td>A game where one player describes an object and the other player tries to identify it based on the description.</td>
      <td>multimodal grounding</td>
      <td>situation model</td>
    </tr>
    <tr style="text-align: center;">
      <td>privateshared</td>
      <td>A game where two players are given different pieces of information and must work together to solve a problem.</td>
      <td>conversational grounding</td>
      <td>discourse model</td>
    </tr>
  </tbody>
</table>
</div>
