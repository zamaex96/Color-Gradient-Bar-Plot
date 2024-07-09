This LaTeX code generates a figure using the `pgfplots` package for creating a bar chart with multiple bars per data point, each representing different metrics. The figure is set to span the entire width of the page (`figure*` environment).

### Description:
- **Packages**: Various packages are imported (`graphicx`, `color`, `textcomp`, `amsmath`, `amsfonts`, `algorithmic`, `pgfplots`, `pgfplotstable`) for graphics, colors, math symbols, algorithms, and plotting.
- **Plot**: A bar chart (`ybar`) is created using `pgfplots`. Three sets of data (`Computational Complexity`, `Power Efficiency`, `Spectral Efficiency`) are plotted against symbolic x coordinates representing different works (`CAP`, `PAPM`, `VPPM`, `DPPM`, `M-PPM`, `M-PAM`, `PWM`, `Proposed`).
- **Legend**: Custom legend formatting is applied with patterns and specific styles (`legend image code`, `legend style`).
- **Captions and Labels**: The figure has a caption (`Comparative analysis with other works`) and a label (`fig_comp`) for reference.

This code generates a detailed and formatted bar chart suitable for academic papers or technical reports. Adjustments to styles and labels can be made as per specific requirements.

![image](https://github.com/zamaex96/Color-Gradient-Bar-Plot/assets/172457177/80a72632-c564-49ae-9db7-6472904852d4)

### Summary of LaTeX Code:

```latex
\usepackage{graphicx,color}
\usepackage{textcomp}
\usepackage{amsmath,amsfonts}
\usepackage{algorithmic}

\usepackage{pgfplots}
\pgfplotsset{width=7cm,compat=1.8}
\usepackage{pgfplotstable}
\usetikzlibrary{patterns}
%\renewcommand*{\familydefault}{\sfdefault}
\usepackage{sfmath}

\begin{document}
\begin{figure*}[ht]
\begin{tikzpicture}
  \centering
  \begin{axis}[
        ybar, axis on top,
        height=8cm, width=18cm,
        bar width=0.3cm,
        ymajorgrids, tick align=inside,
        major grid style={draw=white},
        enlarge y limits={value=.1,upper},
        ymin=0, ymax=6,
        axis x line*=bottom,
        axis y line*=right,
        y axis line style={opacity=1},
        tickwidth=0pt,
        enlarge x limits=true,
        legend image code/.code={%
                    \draw[#1, draw=none] (0cm,-0.1cm) rectangle (0.7cm,0.2cm);
                },  
        legend style={
            draw=none, % ?
            text depth=0pt,
            at={(0.0,1)},
            anchor=north west,
            legend columns=-1,
            column sep=1cm,
            /tikz/column 2/.style={column sep=0pt,font=\bfseries},
            /tikz/every odd column/.append style={column sep=0cm},
        },
        ylabel={Scale},
        symbolic x coords={
           CAP\cite{com30},PAPM\cite{com29},VPPM\cite{com23},DPPM\cite{com24},M-PPM\cite{com28},M-PAM\cite{com27},PWM\cite{com26},Proposed
        },
        xtick=data,
        nodes near coords={
            \pgfmathprintnumber[precision=0]{\pgfplotspointmeta}
        }
    ]
    \addlegendimage{empty legend}
    \addlegendentry{\textbf{}}  
    \addplot [pattern = dots] coordinates {
      (CAP\cite{com30},1)
      (PAPM\cite{com29},1) 
      (VPPM\cite{com23},5)
      (DPPM\cite{com24},1) 
      (M-PPM\cite{com28},5) 
      (M-PAM\cite{com27},5)
      (PWM\cite{com26},1) 
      (Proposed,1) };
    \addlegendentry{Computational Complexity}
    
    \addplot [draw=blue,pattern=horizontal lines light blue] coordinates {
      (CAP\cite{com30},1)
      (PAPM\cite{com29}, 5) 
      (VPPM\cite{com23},2.5)
      (DPPM\cite{com24},5) 
      (M-PPM\cite{com28},5) 
      (M-PAM\cite{com27},1)
      (PWM\cite{com26},2.5) 
      (Proposed,1) };
    \addlegendentry{Power Efficiency}
    
    \addplot [draw=red, pattern color = green, pattern = north west lines] coordinates {
      (CAP\cite{com30},5)
      (PAPM\cite{com29}, 2.5) 
      (VPPM\cite{com23},5)
      (DPPM\cite{com24},5) 
      (M-PPM\cite{com28},1) 
      (M-PAM\cite{com27},5)
      (PWM\cite{com26},1) 
      (Proposed,2.5) };
    \addlegendentry{Spectral Efficiency}
  \end{axis}
\end{tikzpicture}
\caption{Comparative analysis with other works.}
\label{fig_comp}
\end{figure*}
\end{document}


