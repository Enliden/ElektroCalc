# Indholdsfortegnelse
1. [Common](#Common) (4 skabeloner/ 7 færdige formler / 8 tiltænkte formler)
	1. [Netimpedans med RX-forhold](#Netimpedans): FraSkTilZ
	2. [Netimpedans med cosinus](#NetimpedansCosinus): FraSkTilZcos
	3. [Kabel-impedans](#Kabel-impedans): Zkabel
	4. [Impedans-sum](#Z-total): Ztotal
	5. [Strømværdi](#Strømværdi): Iz,min
	6. [Strømværdi Parallelle kabler](#Strømværdi-parallele-kabler): Iz,min,par
	7. [Transformerimpedans](#Transformerimpedans): Ztrafo
	8. [Trafo Fuldlaststrøm](#Fuldlaststrøm-fra-Trafo): TrafoFuldlast
	9. [Strøm henført](#Strøm-henført): I henført
	10. [Sum af Spændingsfald](#Spændingsfaldsum)
2. [Installation](#Installation) (5/7)
	1. [Fasekompensering](#Fasekompensering): faseKOMP-Iny
	2. [1-faset kortslutning](#Ik1f): LV-Ik1f-kA 
	3. [2-faset kortslutning](#Ik2f): LV-Ik2f-kA
	4. [3-faset kortslutning](#Ik3f): LV-Ik3f-kA
	5. [2-faset kortslutning Parallelle sikringssæt](#Kortslutning-Parallele-Sikringssæt): LV-Ik2f,parSikr-kA
	6. [Total maks-impedans](#Ztotal-maks): LV-Ztotal-max
3. [Forsyning](#Forsyning) (0/5)
	1. [Spændingsfald](#Spændingsfald) HV: HV-deltaUnet
	2. [1-faset kortslutning henført](#1f-kortslutning-henført): HV-ZtilIk1-prim
	3. [2-faset kortslutning](#Ik2f-HV): HV-ZtilIk2f
	4. [Kabel-tværsnit til jordskinne-trafo](#S-jordskinne-trafo): S-skinnejord-trafo
	5. [Tid ved inversrelæ](#Tidsberegning-ved-inversrelæ)
	6. [KB kontrol med strøm](#KB-kontrol-strøm)

# Common
## Impendansberegninger
### Netimpedans
```latex
\begin{FraSkTilZ}
	{net,min}{max}{Sk}{6}{0,58}{400}
	%{Impedansnavn, typisk net,min}
	%{Sk max el. min}
	%{Sk}
	%{Sk eksponent: 6 ved Mega}
	%{RX-forhold}
	%{Netspænding}
\end{FraSkTilZ}
```

### NetimpedansCosinus
```latex
\begin{FraSkTilZcos}
	{net,min}{max}{Sk}{6}{0,58}{400}
	%{Impedansnavn, typisk net,min}
	%{Sk max el. min}
	%{Sk}
	%{Sk eksponent: 6 ved Mega}
	%{cosphi}
	%{Netspænding}
\end{FraSkTilZcos}
```

### Transformerimpedans
```latex
\begin{Ztrafo}
	{Un}{Sn}{ek}{Pcu}{Impedansnavn}
	%{Un}{Sn}{ek}{Pcu}{Impedansnavn typisk prim/sek, T3.1}
\end{Ztrafo}
```
### Kabel-impedans
```latex
	\begin{Zkabel}
		{Længde i km}{r}{x}{Un}{kabelNavn}
		%
		%{Længde i km}
		%{r}
		%{x}
		%{Un}  Hvis Un > 400 ==> Ohm
		%{kabelNavn typisk W1}
	\end{Zkabel}
```
### Z-total
```latex
\begin{Ztotal}
	{ 0,2 | 1,88 | 4.5 | 1,6 | 0 | 0 | 0 | 0 | 0 | 0 }{NT}{Net | Trafo | Z3-navn | Z4-navn | Z5-navn}{1 | 1 | 1 | 1 | 1}
	%{ R1 | X1 | R2 | X2 | R3 | X3 | R4 | X4 | R5 | X5 }
	%{Z resultat navn}{Z1 navn | Z2 navn | Z3 navn | Z4 navn | Z5 navn}
	%{Antal_kab 1 | Antal kabler 2 | Antal kabler 3 | Antal kabler 4 | Antal kabler 5}
\end{Ztotal}
```

### ImpedansFraKortslutningseffekt
```latex
\begin{FraIkTilZcos}
	{20}{0.8}{400}{kn,min}{3f,max}
	%{Ik i A}{cosPhi}{Un}{Z navn}{Ik navn}
\end{FraIkTilZcos}
```
## Strømværdi
```latex
\begin{Iz,min}% 7 inputs
	{In}{Kt}{Ks}{Ktm}{Kd}{Kn}{Un} 
	% {In}{Kt}{Ks}{Ktm}{Kd}{Kn}{Un}
	% (spænding bruges tal at bestemme om det er Kd eller Kn} 
\end{Iz,min}
```
## Strømværdi-parallele-kabler
```latex
\begin{Iz,min,par}% 8 inputs
	{In}{Kt}{Ks}{Ktm}{1}{Kn}{400} 
	%(spænding bruges tal at bestemme om det er Kd eller Kn)
	%{In}
	%{Kt}
	%{Ks}
	%{Ktm}
	%{Kd} %bruges nok ikke i El-anlæg
	%{Kn}
	%{Un} %bruges nok ikke i El-anlæg
	%{antal kabler}
	\end{Iz,min}
```
## Fuldlaststrøm-fra-Trafo
```latex
\begin{TrafoFuldlast}{315000}{10500}{1.2}{T3.1 | prim}
%{Sn}{U_trafo}{overlast}{Unavn | I navn}
\end{TrafoFuldlast}
```
## Strøm-henført
```latex
\begin{I-henført}{I}{10,5}{0,42}{Inavn}{0}
	%{I strøm}{Uprim}{Usek}{Inavn}{0 = sek til prim. 1 = prim til sek}
\end{I-henført}
```

## Spændingsfaldsum
```latex
\begin{spændingsfaldsum}
	{ 0.01 | 0.02 | 0 | 0 | 0 }{ samlet }{1 | 2 | 3 | 4 | 5}
	%{ dU1 | dU2 | dU3 | dU4 | dU5 }
	%{dU-resultat navn}
	%{dU1 navn | dU2 navn | dU3 navn | dU4 navn | dU5 navn}
\end{spændingsfaldsum}
```
## Faktisk-Spænding
```latex
\begin{faktiskspænding}
	{400}{0.05}{ n1 | n2 | n }
	%{Spænding}{spændingsfald}{ navn startspænding | navn slutspænding | fase eller netspænding}
\end{faktiskspænding}
```
# Installation
## Ztotal-max

```latex
## Ztotal-maks
```latex
\begin{LV-Ztotal-max}
	{ 1 | 2 | 3 | 4| 5 | 0 | 0 | 0 | 0 | 0 }
	{Z resultat navn}{Z1 navn | Z2 navn | Z3 navn | Z4 navn | Z5 navn} 
	{Antal_kab 1 | Antal kabler 2 | Antal kabler 3 | Antal kabler 4 | Antal kabler 5}
	% { R1 | X1 | R2 | X2 | R3 | X3 | R4 | X4 | R5 | X5 }
	% {Z resultat navn}{Z1 navn | Z2 navn | Z3 navn | Z4 navn | Z5 navn}
	% {Antal_kab 1 | Antal kabler 2 | Antal kabler 3 | Antal kabler 4 | Antal kabler 5}
\end{LV-Ztotal-max}
```

## Fasekompensering
```latex
\begin{faseKOMP-Iny}
	{540,8}{0,81}{0,9}{10}{A1}
	%{I_belastning}{cosphi_før}{cosphi_ønsket}{Q_batteristørrelse[kVAR]}{Tavlenavn}
\end{faseKOMP-Iny}
```
## Kortslutning-Parallele-Sikringssæt
```latex
\begin{LV-Ik2f,parSikr-kA}
	{R net + trafo | X net + trafo |R kabler |X kabler }{3}{min |N+T,min}{w1}                      
	%
	%{ R net + trafo | X net + trafo | R kabler | X kabler }{maks/min | net-trafo-navn | kabel-navn}
	%impedanser i milliohm
	% DET ER EN GOD IDE MED MELLEMRUM OMKRING PIPES!
\end{LV-Ik2f,parSikr-kA}
```
## Ik3f
```latex
\begin{LV-Ik3f-kA}
	{R net + trafo |X net + trafo |R kabler |X kabler }{max}{N+T,min}{w1}                      
	%{ R net + trafo | X net + trafo | R kabler | X kabler }{maks/min | net-trafo-navn | kabel-navn}
	% impedanser i milliohm
	% Ved minimum-kortslutning: Brug maks impedanser
\end{LV-Ik3f-kA}
```


## Ik2f
```latex
\begin{LV-Ik2f-kA}
	{R net + trafo |X net + trafo |R kabler |X kabler }{max}{N+T,min}{w1}                      	
	%{ R net + trafo | X net + trafo | R kabler | X kabler }{maks/min | net-trafo-navn | kabel-navn}
	% impedanser i milliohm
	% Ved minimum-kortslutning: Brug maks impedanser
\end{LV-Ik2f-kA}
```

## Ik1f

```latex
\begin{LV-Ik1f-kA}
	{R net + trafo |X net + trafo |R kabler |X kabler }{max}{N+T,min}{w1}                      
	%{ R net + trafo | X net + trafo | R kabler | X kabler }{maks/min | net-trafo-navn | kabel-navn}
	% impedanser i milliohm
	% Ved separat PE-leder: Beregn Z-total = Znet + Ztrafo + Zw1 + ... + Zpe
	%     og sæt det ind i første paramter Rnet + trafo osv.
	% Ved minimum-kortslutning: Brug maks impedanser
\end{LV-Ik1f-kA}
```





```latex
\begin{LV-ZtilIk1f-min}
{ Rnet | Xnet | Rtrafo | Xtrafo |Rkab1 | Xkab1 | Rkab2 | Xkab2 | Rkab3 | Xkab3 }{Ik,navn | netnavn | trafonavn | kabel1navn | kabel2navn| kabel3navn}
%{ Rnet | Xnet | Rtrafo | Xtrafo | Rkab1 | Xkab1 | Rkab2 | Xkab2 | Rkab3 | Xkab3 }
%{Ik,navn | netnavn | trafonavn | kabel1navn | kabel2navn | kabel3navn}
\end{LV-ZtilIk1f-min}
```

# Forsyning
## Spændingsfald
```latex
\begin{HV-deltaUnet}
	{}                       %{Ib}
	{}                       %{R}
	{}                       %{X}
	{}                       %{cosPhi}
	{}                       %{U navn 
{}                       % | Ib navn}
\end{HV-deltaUnet}
```

## Ik2f-HV
```latex
\begin{HV-ZtilIk2f}{10000}{ 0,45 | 2,67 | 0,47 | 0,19 | 0 | 0 | 0 | 0 | 0 | 0 }{Ik2f,T0,min | NT,max | kabel,Wtot | Z3 navn | Z4 navn | Z5 navn}
%{Un}{ R1 | X1 | R2 | X2 | R3 | X3 | R4 | X4 | R5 | X5 }{Ik,navn | Z1 navn | Z2 navn | Z3 navn | Z4 navn | Z5 navn}
\end{HV-ZtilIk2f}
```

## 1f-kortslutning-henført
```latex
\begin{HV-ZtilIk1-prim}
	{10000}{ R1 | X1 | R2 | X2 | R3 | X3 }{Ik,navn | Z1 navn | Z2 navn | Z3 navn}
	%{Un} formlen bruges kun ved el-anlæg, så Un=10000
	%{ Rnet | Xnet | Rkabel | Xkabel | Rtrafo | Xtrafo } 
	%{Ik,navn | Znet navn | Zkabel navn | Ztrafo navn}
\end{HV-ZtilIk1-prim}
```

## S-jordskinne-trafo
```latex
\begin{S-skinnejord-trafo}
{}       %{Ik}
{}       %{udløsningstid}
{}       %{start temp}
{}       % {1/2 = relæ/sikring}
{}       % {Ik,navn}
{}        % {tid navn}
{}        %{tværsnit navn}
\end{S-skinnejord-trafo}
```

### Tidsberegning-ved-inversrelæ
```latex
\begin{tid-inversrelæ}
	{0.5}{0.14}{50}{75}{0,02}{ Q1 | b }
	%{K} {C} {I} {I-hak} {a } { tidnavn | strømnavn }
\end{tid-inversrelæ}
```

### KB-kontrol-strøm
```latex
\begin{KB-kontrol-strøm}
	{600}{5000}{1}{0.1}{k,1s,skærm | k3,max | >> | e }
	%{Ik1s,leder}{ik3max}{t-hak-hak}{t egen}{k,1s,skærm | k3,max | t-hak navn | t-e navn }
	%{Ik1s,skærm}{ik2max}{t-hak-hak}{t egen}{k,1s,skærm | k3,max | t-hak navn | t-e navn }
\end{KB-kontrol-strøm}
```


# Skabeloner
## Kabel dim
```latex
\textbf{Nedgravet i jord uden samlet fremføring, 15 grader, 2 termiskmodstand}
Der nedgraves XLPE kabel, men det dimensioneres som PVC for ikke at udtørre jorden.
\begin{Iz,min}{Ib}{Kt}{Ks}{Ktm}{Kd}{Kn}{Un}
\end{Iz,min}

\begin{itemize}
	\item Tabel A.52.3 $\Rightarrow$ 72
	\item Tabel B.52.1 $\Rightarrow$ 6
	\item Tabel B.52.4 $\Rightarrow$ 8
\end{itemize}
Det er ikke muligt at få et stort nok tværsnit derfor lægges X parralel kabler.

\begin{Iz,min,par}{Ib}{Kt}{Ks}{Ktm}{Kd}{Kn}{Un}{Antal kabler}
\end{Iz,min,par}

\begin{itemize}
	\item Tabel A.52.3 $\Rightarrow$ 72
	\item Tabel B.52.1 $\Rightarrow$ 6
	\item Tabel B.52.4 $\Rightarrow$ 8
\end{itemize}
Dette giver et tværsnit på 3//4x240$mm^2$ $[250A > 220,13A]$
```

## HV KB skærm og leder
```latex
%2faset for skæm, 3 faset for leder
\textbf{Leder}
\begin{equation*}
	\begin{split}
	I_{k1s,leder} &\geq I_{k3f,T0,max} \cdot \sqrt{t_{>>} + t_{egen}}\\
	14200 A &\geq 6601A \cdot \sqrt{0.3 + 0.1}\\
	14200 A &\geq 4175 A \Rightarrow OK!\\	
	\end{split}
\end{equation*}
```

## Figur
```latex
\begin{figure}[H]
    \centering
    \includegraphics[width=\textwidth ,height=15cm , keepaspectratio=true]{Figurer/%|}
    \caption{Figur}
    \label{fig:fig}
\end{figure}
```

## Maksimal afbryder
```latex
\begin{table}[H]
	\begin{tabular}{l|l}
		NSX630F & Micrologic 2 \\ \hline
		$I_N$ 		= 630A  	& $I_o$		= 450A              \\
		$I_{cu}$	= 36kA		& $I_r$		= 405A = $I_{o} \cdot x$        \\
		$I_{cs}$ 	= ?    		& $I_{sd}$	= 2500A = $I_{r} \cdot x$            \\
								& $I_i$     = ?    
	\end{tabular}
\end{table}
```

```latex

```

```latex

```

```latex

```

```latex

```


## Selektivtet

### Smelte-smelte
s. 174. Ligning 4.1
```latex
$$
	I^2t_{up,smelte} \cdot 0,8 \ge I^2 t_{down, lysbue+smelte}
$$
```

### ParallelSmelte-Smelte
s. 176, ligning 4.2
```latex
$$
	I^2t_{up,smelte} \cdot 0,8 \cdot n^2 \ge I^2 t_{down, lysbue+smelte}
$$
```

### MA(A)-MA(B)
Bog 6, s 181.
- Strømselektivitet (naturlig selektivitet)
- Tidsselektivtet

Qup --> Qdown --> Appliance
	A --> B           --> C
```latex
\begin{align}
		I_{k,maks(C)} &< I_{m,up} \le \frac{I_{k,min(B)} }{1,2} \\
	2\cdot I_{m,down} &< I_{m,up} \\
			I_{sd,up} &< I_{m,up} 
\end{align}
```

Ikke-strømbegrænsende lader sig gøre. S. 182

### MA - Smelte
s.194

```latex
$$
	I_{eff,cut-off,F,down} < I_{m,up} < \frac{I_{k,min(B)} }{1,2}
$$
```

### Smelte - MA
s. 196
**Selektivitet ved Overbelastning:** Afstand på 1 sekund på strøm-tidskurven mellem $I_{r,down}$-udløserens *øvre* grænsekurve og smeltesikringskurven.

**Selektivtet ved kortslutning:**
```latex
$$
	I^2t_{up,smelte} \cdot 0,8 \ge I^2 t_{maksimalafrbryder,down}
$$
```

### Smelte-HåndbetjentMotorværn(m.kortslutningsudløser)
```latex
$$
	I^2t_{up,smelte} \cdot 0,8 \ge I_{kmaks(B),down}^2 t_{down, HMV} \longrightarrow \mathbb{OK: Total selektivitet}
$$
```
Gennemslipsenergien for down findes i datablad ved $I_{k,maks(B)}$
Der kan opnås delvis selektivtet ved
```latex
$$
	I^2t_{up,smelte} \cdot 0,8 \ge I_{kmaks(C),down}^2 t_{down, HMV} \longrightarrow \mathbb{OK: Total selektivitet}
$$
```
### Smelte-Automatsikring
```latex
$$
	I^2t_{up,smelte} \cdot 0,8 \ge I_{kmaksB}^2 t_{down}
$$
```
