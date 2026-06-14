(Title page only -- content to be added.)

Title: **Decision Theory**
Author: Daniel C
Date: (placeholder)

- For the reflective AIXI portion just take and paraphrase (and credit Cole Wyeth's slides) from the embedded AIXI slides in agent foundations sources (start from self-modelling failures and AIXI)

- The second half will be on open source game theory, commitment races and safe pareto-improvements

- Starting point:
  
  - Brief explanation of regular game theory
  
  - Lobian cooperation and epsilon fairbot (search online)
  
  - And then open source game theory is the next step from that:
    
    - Emphasize two desiderata: Cooperate with your own copy, and inexploitability (opponent can't become better off by making you worse off)
    
    - Open source game theory can be thought of as a form of conditional commitment: Regular game theory fails because utility depends on joint action, but you are uncertain about the opponent's action and vice versa. Conditional commitment= "I commit to X conditional on opponent making conditional commitment Y". So 1. the conditional part allows you to remain unexploitable and 2. Commitment part means that you can legibly commit to cooperative outcomes (so that you can fulfill the "conditions" of your opponent's conditional commitment)
  
  - Commitment race
    
    - [The Commitment Races problem — LessWrong](https://www.lesswrong.com/posts/brXr7PJ2W4Na2EW2q/the-commitment-races-problem)
    
    - Commitment race and s-risks
    
    - Influencer vs responder:
      
      - Responder: Run opponent's program and obtain opponent's output/action, argmax my utility according to that action
      
      - Influencer: Assume that opponent is a responder, argmax my utility. Select the point on the pareto-frontier that's best for me and worse off for my opponent
      
      - best response is not always the best response
    
    - Generalized commitment race
      
      - Entanglement is the obstacle
    
    - Entanglement-free SPI
      
      - https://drive.google.com/file/d/1seiEVlR7zFpAdpixDV4V1eI1tktJJINT/view?usp=sharing (read this, make sure you deeply understand what is going on, but explain in a more clarifying way than I did)
      
      - Entanglement is the reason why agents might not be incentivized to make pareto-improvement, so we use a different program (the renegotiation program) that doesn't suffer from entanglement to make pareto improvement instead
      
      - Read the doc and explain why updating on the renegotiation program first removes the disincentive to making pareto improvements
      
      - Write the algorithm formalism based on the doc, but you may rewrite the formalism in a much cleaner way making sure that you preserve the meaning
      
      - Explain that usually if you have a procedure where one agent moves first and the other moves first. You get "influencer responder" dynamic  where the agent that moves first can pick the point on the pareto frontier best for itself and worse for the opponent, while the opponent just plays the best response. We don't run into this problem here (even though renegotiation program is played before the default program) as the renegotiation program can only make pareto improvement (so it can't make the other agent worse off)
    
    - Explain and credit the original paper on SPIs: [[2403.05103] Safe Pareto Improvements for Expected Utility Maximizers in Program Games](https://arxiv.org/abs/2403.05103). 
    
    - Explain that the original paper relies on an assumption called "participation independence" where agents does not behave differently in the SPI game compared to the default game
    
    - The problem is that if I know that SPI will be implemented, I know that whatever conflict outcome that might happen will be pareto-improved upon, so the stakes aren't as high, and I might adjust my strategy and become more hawkish. This might defeat my opponent's incentive for using SPI in the first place (because my opponent anticipates that I become more hawkish if SPI is implemented)
    
    - Entanglement-free SPI solves cheating problem and removes reliance on participation independence by allowing renegotiation program to condition on default program (so renegotiation can "detect" cheating), while the sequential structure avoids introducing a commitment race on its own
    
    - However, the original paper on SPI is able to prove a nice bound on minimum utility given the participation independence assumption, and removing this assumption removes the bound (so entanglement-free cannot achieve the same bound on weaker assumptions)  
