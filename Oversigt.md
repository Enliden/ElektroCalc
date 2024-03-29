# Indholdsfortegnelse
1. [Common](#Common) (4 skabeloner/ 7 færdige formler / 8 tiltænkte formler)
	1. [Netimpedans med RX-forhold](#Netimpedans): FraSkTilZ
	2. [Netimpedans med cosinus](#NetimpedansCosinus): FraSkTilZcos
	3. [Netimpedans fra Ik](#NetimpedansFraIk)
	4. [Netimpedans fra Ik med cosinus](#NetimpedansFraIk-cos)
	5. [Sumstrøm](#Sumstrøm)
	6. [Kabel-impedans](#Kabel-impedans): Zkabel
	7. [Impedans-sum](#Z-total): Ztotal
	8. [Strømværdi](#Strømværdi): Iz,min
	9. [Strømværdi Parallelle kabler](#Strømværdi-parallele-kabler): Iz,min,par
	10. [Transformerimpedans](#Transformerimpedans): Ztrafo
	11. [Trafo Fuldlaststrøm](#Fuldlaststrøm-fra-Trafo): TrafoFuldlast
	12. [Strøm henført](#Strøm-henført): I henført
	13. [Sum af Spændingsfald](#Spændingsfaldsum)
2. [Installation](#Installation) (5/7)
	1. [Fasekompensering](#Fasekompensering): faseKOMP-Iny
	2. [1-faset kortslutning](#Ik1f): LV-Ik1f-kA 
	3. [2-faset kortslutning](#Ik2f): LV-Ik2f-kA
	4. [3-faset kortslutning](#Ik3f): LV-Ik3f-kA
	5. [2-faset kortslutning Parallelle sikringssæt](#Kortslutning-Parallele-Sikringssæt): LV-Ik2f,parSikr-kA
	6. [Total maks-impedans](#Ztotal-maks): LV-Ztotal-max
	7. [KB-kontrol-LV](#LV-KB-kontrol)
	8. [Spændingsfald[[#LV-spændingsfald]](#LV-spændingsfald)
3. [Forsyning](#Forsyning) (0/5)
	1. [Spændingsfald](#Spændingsfald) HV: HV-deltaUnet
	2. [1-faset kortslutning henført](#1f-kortslutning-henført): HV-ZtilIk1-prim
	3. [2-faset kortslutning](#Ik2f-HV): HV-ZtilIk2f
	4. [Kabel-tværsnit til jordskinne-trafo](#S-jordskinne-trafo): S-skinnejord-trafo
	5. [Tid ved inversrelæ](#Tidsberegning-ved-inversrelæ)
	6. [KB kontrol med strøm](#KB-kontrol-strøm)
	7. [Lækstrøm per fase](#lækstrøm)

# Common
## Impendansberegninger
### Netimpedans
```latex
\begin{FraSkTilZ}
	{net,min}{max}{120}{6}{0,58}{400}
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

## NetimpedansFraIk
```latex
\begin{FraIkTilZ}{4000}{0.5}{400}{NT}{NT}
	%{Ik}{cosPhi}{Un}{Z navn}{Ik navn}
\end{FraIkTilZ}
```
## NetimpedansFraIk-cos
```latex
\begin{FraIkTilZcos}{4000}{0.5}{400}{NT}{NT}
	%{Ik}{cosPhi}{Un}{Z navn}{Ik navn}
\end{FraIkTilZcos}
```

## Sumstrøm
```latex
	\begin{Itotal}
		{2 | 10 | 4 | 20 | 6 | 30 | 8 | 40 | 10 | 50 }
		{sum}
		{ et | to | tre | fire | fem }
		% { I1 | angle UDEN fortegn| I2 | angle2 | I3 | angle3 | I4 | angle4 | I5 | angle }
		% {I resultat navn}
		% {I1 navn | I2 navn | I3 navn | I4 navn | I5 navn}
		% {Korrektion/start/inrush | samme 2 | samme 3 | samme 4 | samme 5}
	\end{Itotal}
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
		{Længde i km}{r}{x}{Un}{W1}
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
\begin{TrafoFuldlast}
	{315000}{10500}{1.2}{N,T1| 1/1,T1,prim}
	%{Sn}{U_trafo}{overlast}{Unavn | I navn}
\end{TrafoFuldlast}
```

## Strøm-henført
```latex
\begin{I-henført}
	{360.96}{10,5}{0,42}{k1,min}{1}
	%{I strøm}{Uprim}{Usek}{Inavn}{0 = prim til sek. 1 = sek til prim}
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
	{ 3.02 | 8.1 | 305.6 | 12.48 }{ k1f,min | NT,max | W26}                      
	%{ R net + trafo | X net + trafo | R kabler | X kabler }{strøm navn maks/min | net-trafo-navn | kabel-navn}
	% impedanser i milliohm
	% Ved separat PE-leder: Beregn Z-total = Znet + Ztrafo + Zw1 + ... + Zpe
	%     og sæt det ind i første paramter Rnet + trafo osv.
	% Ved minimum-kortslutning: Brug maks impedanser
\end{LV-Ik2f-kA}
```

## Ik1f

```latex
\begin{LV-Ik1f-kA}
	{ 3.02 | 8.1 | 305.6 | 12.48 }{ k1f,min | NT,max | W26}                      
	%{ R net + trafo | X net + trafo | R kabler | X kabler }{strøm navn maks/min | net-trafo-navn | kabel-navn}
	% impedanser i milliohm
	% Ved separat PE-leder: Beregn Z-total = Znet + Ztrafo + Zw1 + ... + Zpe
	%     og sæt det ind i første paramter Rnet + trafo osv.
	% Ved minimum-kortslutning: Brug maks impedanser
\end{LV-Ik1f-kA}
```

## LV-KB-kontrol
```latex
\begin{KB-kontrol-energi}
	{2,6}{3}{243}{13}{  | X | W1 }
	%{aflæst energi}{eksponent}{k-værdi}{tværsnit}{I^2t navn | k navn | tværsnit navn}
\end{KB-kontrol-energi}
```

## LV-spændingsfald
```latex
\begin{LV-deltaU}
	{130}{0,206}{0,081}{0,9}{1}{W1 | T2}
	%{Ib}{R}{X}{cosPhi}{antal faser}{U navn | Ib navn}
\end{LV-deltaU}
```

## Tleder 
```latex
\begin{HV-KBtid-leder}{3000}{5000}{0,4}{leder,>> | k3f | k,1s,leder, W1 }
	%{Ik3,max}{ik1s}{t egen}%{leder,>> | k3f | k,1s,leder, W1 }
\end{HV-KBtid-leder}
```

## Tskærm
```latex
\begin{HV-KBtid-leder}{3000}{5000}{0,4}{skærm,>> | k3f | k,1s,skærm, W1 }
	%{Ik3,max}{ik1s}{t egen}%{leder,>> | k3f | k,1s,leder, W1 }
\end{HV-KBtid-leder}
```

# Forsyning
## Spændingsfald
```latex
\begin{HV-deltaUnet}{130}{0,206}{0,081}{0,9}{W1 | T2}
	%{Ib}{R}{X}{cosPhi}{U navn | Ib navn}
\end{HV-deltaUnet}
```

## Ik2f-HV
```latex
\begin{HV-ZtilIk2f}{10000}{ 0,45 | 2,67 | 0,47 | 0,19 | 0 | 0 | 0 | 0 | 0 | 0 }{Ik2f,T0,min | NT,max | kabel,Wtot | Z3 navn | Z4 navn | Z5 navn}
%{Un}{ R1 | X1 | R2 | X2 | R3 | X3 | R4 | X4 | R5 | X5 }{Ik,navn | Z1 navn | Z2 navn | Z3 navn | Z4 navn | Z5 navn}
\end{HV-ZtilIk2f}
```

## Ik3f-HV
```latex
\begin{HV-ZtilIk3f}{10000}{ 0,45 | 2,67 | 0,47 | 0,19 | 0 | 0 | 0 | 0 | 0 | 0 }{Ik3f,T0,min | NT,max | kabel,Wtot | Z3 navn | Z4 navn | Z5 navn}
%{Un}{ R1 | X1 | R2 | X2 | R3 | X3 | R4 | X4 | R5 | X5 }{Ik,navn | Z1 navn | Z2 navn | Z3 navn | Z4 navn | Z5 navn}
\end{HV-ZtilIk3f}
```


## 1f-kortslutning-henført
```latex
\begin{HV-ZtilIk1-prim}
	{10000}{ 0,12 | 0,82 | 0,21 | 0,14 | 0 | 0 }{1f-n,sek | KN,max | R2,240 | z3}
	%{Un} formlen bruges kun ved el-anlæg, så Un=10000
	%{ Rnet | Xnet | Rkabel | Xkabel | Rtrafo | Xtrafo } 
	%{Ik,navn | Znet navn | Zkabel navn | Ztrafo navn}
\end{HV-ZtilIk1-prim}
```

```latex
\begin{3f-2f}{540}{1}{T1,max}
	%{Ik strøm}{2f = 0 , 3f = 1}{Inavn uden ikxf, typisk trafonavn og max}
\end{3f-2f}
```

## S-jordskinne-trafo
```latex
\begin{S-skinnejord-trafo}
{5414.35}       %{Ik}
{0.02}       %{udløsningstid}
{40}       %{start temp}
{2}       % {1/2 = relæ/sikring}
{k2f,T1,min}       % {Ik,navn}
{smelte}        % {tid navn}
{BJ}        %{tværsnit navn}
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

## Lækstrøm
```latex
\begin{HV-lækstrøm-pr-fase}{10000}{20}{0,44}{50}{tot,radial}
	%{Un}{længde af kabler}{Kapitans pr km}{frekvens}{kabel navn}
\end{HV-lækstrøm-pr-fase}
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
