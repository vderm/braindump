+++
title = "Temporal Difference Learning"
author = ["Jethro Kuan"]
lastmod = 2020-06-07T17:27:53+08:00
draft = false
+++

## Backlinks {#backlinks}

- [Q-Learning]({{< relref "q_learning" >}})
- [Neuroscience and Reinforcement Learning]({{< relref "neuroscience_rl" >}})
- [Reinforcement Learning ⭐]({{< relref "reinforcement_learning" >}})
- [The Paths Perspective on Value Learning]({{< relref "the_paths_perspective_on_value_learning" >}})
- [Options Framework]({{< relref "options_framework" >}})

Observe samples \\(\left(s_t, a_t, r_t, s\_{t+1} \right)\\). If value
estimates are accurate, the following must hold:

\begin{equation}
V(s_t) = r_t + \gamma V(s\_{t+1})
\end{equation}

If not, there is a TD error:

\begin{equation}
\gamma = r_t + \gamma V(s\_{t+1}) - V(s_t)
\end{equation}

To learn better estimates - minimize $&gamma; $ TD(0):

\begin{equation}
V(s) \leftarrow V(s) + \alpha \left( r_t + \gamma V(s\_{t+1}) - V(s_t) \right)
\end{equation}
