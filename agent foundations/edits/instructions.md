# Instructions

Write editing instructions here as bullet points. Claude Code will read these,
apply the corresponding changes to the LaTeX project, compile, and update the
markdown mirror.

Examples:

- "Add a bullet to the Löbian Obstacle slide explaining the finite descent problem"
- "Rewrite the FDT slide to lead with the twin PD example before stating the general principle"
- "Create a new slide after Descriptive Agent Foundations on selection theorems"

---

(Write instructions below this line)

- Write a self-contained but rigorous lecture notes (10-15 pages, new project) on "Optimization and thermodynamics", the relevant sources are in agent foundations/sources/algorithmic thermodynamics. Some notes on how the lecture notes should be created
  
  - Be self-contained and rigorous and emphasize conceptual clarity. Use formalisms to improve conceptual clarity but not in a way that overwhelms people
  
  - Be very careful and rigorous about the algorithmic thermodynamics stuff, the algorithmic thermodynamics content should center on the "Algorithmic thermodynamics and three types of optimization" post, but use the original "foundations of algorithmic thermodynamics" to back things up formally (to the extent of not making it hard to read) and provide the necessary details for context. Especially focus on the connection between algorithmic thermodynamics and embedded agency, where regular stochastic thermodynamics definition of entropy requires a subjective distribution and treats probabilistic knowledge as exogenous (traditional equilibrium thermodynamics is then not applicable in out of equilibrium settings), whereas algorithmic thermodynamics makes it endogenous, where agents that have more subjective probability knowledge about the environment gets to perform more optimization because it has more algorithmic mutual information with the environment (and mutual info is the resource for optimization according to the touchette and lloyd bound). You can read about this in both algorithmic thermodynamics pdfs
  
  - Use the last few slides from the agency_presentation which talks about optimization and thermodynamics to determine the focus of the content.
  
  - Try to integrate all sources into a coherent theme that is connected, but make sure that the connections you make is rigorous and precise
  
  - You may use "Decision_Theory_CDT_to_UDT_1_1 (1).pdf" from decision theory sources as a minimal baseline for quality 
