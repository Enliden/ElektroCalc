# Indholdsfortegnelse
1. [Common](#Common) (4 skabeloner/ 7 færdige formler / 8 tiltænkte formler)
	1. [Netimpedans med RX-forhold](#Netimpedans): FraSkTilZ
	2. [Netimpedans med cosinus](#Netimpedans med cosiunus): FraSkTilZcos
	3. [Kabel-impedans](#Kabel-impedans): Zkabel
	4. [Impedans-sum](#Z-total): Ztotal
	5. [Strømværdi](#Strømværdi): Iz,min
	6. [Strømværdi Parallelle kabler](#Strømværdi-parallele-kabler): Iz,min,par
	7. [Transformerimpedans](#Transformerimpedans): Ztrafo
	8. [Trafo Fuldlaststrøm](#Fuldlaststrøm-fra-Trafo): TrafoFuldlast
2. [Installation](#Installation) (5/7)
	1. [Fasekompensering](#Fasekompensering): faseKOMP-Iny
	2. [1-faset kortslutning](#Ik1f): LV-Ik1f-kA    og  LV-ZtilIk1f-min
	3. [2-faset kortslutning](#Ik2f): LV-Ik2f-kA
	4. [3-faset kortslutning](#Ik3f): LV-Ik3f-kA
	5. [2-faset kortslutning Parallelle sikringssæt](#Kortslutning-Parallele-Sikringssæt): LV-Ik2f,parSikr-kA
	6. [Total maks-impedans](#Ztotal-maks): LV-Ztotal-max
3. [Forsyning](#Forsyning) (0/5)
	1. [Spændingsfald](#Spændingsfald) HV: HV-deltaUnet
	2. [1-faset kortslutning henført](#1f-kortslutning-henført): HV-ZtilIk1-prim
	3. [2-faset kortslutning](#Ik2f-HV): HV-ZtilIk2f
	4. [Kabel-tværsnit til jordskinne-trafo](#S-jordskinne-trafo): S-skinnejord-trafo
	5. [Kortslutning](#kortslutning): ZtilIkHV
# Common
## Netimpedans
\begin{FraSkTilZ}
{net,min}{max}{Sk}{6}{0,58}{400}
%{Impedansnavn, typisk net,min}
%{Sk max el. min}
%{Sk}
%{Sk eksponent: 6 ved Mega}
%{RX-forhold}
%{400}
\end{FraSkTilZ}

$$\begin{align*}
        \overline{Z}_{net} &= \frac{U_n^2}{S_{kn,max}} \angle \text{arccot} \left( \frac{R}{X}\right)\\
        &= \frac{10000^2}{320 \cdot 10^3} \angle \text{arccot} \left( 0,5 \right)\\
		&= 312.5 \angle 63.4 \degree 
\end{align*}
$$

\begin{FraSkTilZcos}
{net,min}{max}{Sk}{6}{0,58}{400}
%{Impedansnavn, typisk net,min}
%{Sk max el. min}
%{Sk}
%{Sk eksponent: 6 ved Mega}
%{cosphi}
%{400}
\end{FraSkTilZcos}
## Netimpedans med cosinus
## Transformerimpedans
\begin{Ztrafo}
{Un}{Sn}{ek}{Pcu}{Impedansnavn}
%{Un}{Sn}{ek}{Pcu}{Impedansnavn typisk prim/sek, T3.1}
\end{Ztrafo}

## Kabel-impedans
\begin{Zkabel}
{Længde i km}{r}{x}{Un}{kabelNavn}
%
%{Længde i km}
%{r}
%{x}
%{Un}  Hvis Un > 400 ==> Ohm
%{kabelNavn typisk W1}
\end{Zkabel}

## Z-total
\begin{Ztotal}{ 0,2 | 1,88 | 4.5 | 1,6 | 0 | 0 | 0 | 0 | 0 | 0 }{NT}{Net | Trafo | Z3-navn | Z4-navn | Z5-navn}{1 | 1 | 1 | 1 | 1}
	%{ R1 | X1 | R2 | X2 | R3 | X3 | R4 | X4 | R5 | X5 }{Z resultat navn}{Z1 navn | Z2 navn | Z3 navn | Z4 navn | Z5 navn}{Antal_kab 1 | Antal kabler 2 | Antal kabler 3 | Antal kabler 4 | Antal kabler 5}
\end{Ztotal}
## Strømværdi
\begin{Iz,min}% 7 inputs
{In}{Kt}{Ks}{Ktm}{Kd}{Kn}{Un} %(spænding bruges tal at bestemme om det er Kd eller Kn)
%{In}{Kt}{Ks}{Ktm}{Kd}{Kn}{Un} 
\end{Iz,min}

## Strømværdi-parallele-kabler
\begin{Iz,min,par}% 8 inputs
{In}{Kt}{Ks}{Ktm}{1}{Kn}{400} %(spænding bruges tal at bestemme om det er Kd eller Kn)
%{In}
%{Kt}
%{Ks}
%{Ktm}
%{Kd} %bruges nok ikke i El-anlæg
%{Kn}
%{Un} %bruges nok ikke i El-anlæg
%{antal kabler}
\end{Iz,min}

## Fuldlaststrøm-fra-Trafo
\begin{TrafoFuldlast}
{Sn}{U_trafo}{trafoNavn}
%{Sn}{U_trafo}{typisk T1,prim}
\end{TrafoFuldlast}






# Installation
## Ztotal-max


`\begin{LV-Ztotal-max}
`{ R1                        % Resistans 1 i mili ohm
`| X1                        % Reaktans 1`
`| R2                        % Resistans 2`
`| X2                        % Reaktans 2`
`| R3                        % Resistans 3 `
`| X3                        % Reaktans 3`
`| R4                        % Resistans 4`
`| X4                        % Reaktans 4`
`| R5                        % Resistans 5`
`| X5 }                      % Reaktans 5`
`{ Total}                   % Navn på total-resistans`
`{ Net                       % Navn på Z1`
`| Trafo                    % Navn på Z2`
`| W1                       % Navn på Z3`
`| W2                       % Navn på Z4 `
`| W3}                      % Navn på Z5`
`{ 1                           % Parallele 1`
`| 1                           % Parallele 2`
`| 1                           % Parallele 3`
`| 1                           % Parallele 4`
`| 1}                          % Parallele 5``
`\end{LV-Ztotal-max}`

Komprimeret version

`\begin{LV-Ztotal-max}`
`{ R1 | X1 | R2 | X2 | R3 | X3 | R4 | X4 | R5 | X5 }{Z resultat navn}{Z1 navn | Z2 navn | Z3 navn | Z4 navn | Z5 navn}{Antal_kab 1 | Antal kabler 2 | Antal kabler 3 | Antal kabler 4 | Antal kabler 5}`
`% { R1 | X1 | R2 | X2 | R3 | X3 | R4 | X4 | R5 | X5 }{Z resultat navn}{Z1 navn | Z2 navn | Z3 navn | Z4 navn | Z5 navn}{Antal_kab 1 | Antal kabler 2 | Antal kabler 3 | Antal kabler 4 | Antal kabler 5}`
`\end{LV-Ztotal-max`}
## Fasekompensering
\begin{faseKOMP-Iny}{540,8}{0,81}{0,9}{10}{A1}
%{I_belastning}{cosphi_før}{cosphi_ønsket}{Q_batteristørrelse[kVAR]}{Tavlenavn}
\end{faseKOMP-Iny}
## Kortslutning-Parallele-Sikringssæt
\begin{LV-Ik2f,parSikr-kA}
{R net + trafo |  % net+trafo resistans
X net + trafo |    % net+trafo induktans
R kabler |            % Kabelresistans
X kabler }            % Kabelinduktans
{3}                         % antal ledninger
{min |                    % min el. maks strøm
{N+T,min}            % Net og trafo navn
{w1}                      % Kabelnavn
%
%
%{ R net + trafo | X net + trafo | R kabler | X kabler }{maks/min | net-trafo-navn | kabel-navn}
%impedanser i milliohm
% DET ER EN GOD IDE MED MELLEMRUM OMKRING PIPES!
\end{LV-Ik2f,parSikr-kA}

## Ik3f
\begin{LV-Ik3f-kA}
{R net + trafo |  % net+trafo resistans
X net + trafo |    % net+trafo induktans
R kabler |            % Kabelresistans
X kabler }            % Kabelinduktans
{max}                   % maks eller min
{N+T,min}            % Net og trafo navn
{w1}                      % Kabelnavn
%
%
%{ R net + trafo | X net + trafo | R kabler | X kabler }{maks/min | net-trafo-navn | kabel-navn}
% impedanser i milliohm
\end{LV-Ik3f-kA}


## Ik2f
```latex
\begin{LV-Ik2f-kA}
	{R net + trafo |  % net+trafo resistans
	X net + trafo |    % net+trafo induktans
	R kabler |            % Kabelresistans
	X kabler }            % Kabelinduktans
	{max}                   % maks eller min
	{N+T,min}            % Net og trafo navn
	{w1}                      % Kabelnavn
	%
	%
	%{ R net + trafo | X net + trafo | R kabler | X kabler }{maks/min | net-trafo-navn | kabel-navn}
	% impedanser i milliohm
\end{LV-Ik2f-kA}
```

## Ik1f
<<<<<<< HEAD


# Anlæg
## 1f-kortslutning på sekundærside henført
=======
\begin{LV-Ik1f-kA}
{R net + trafo |  % net+trafo resistans
X net + trafo |    % net+trafo induktans
R kabler |            % Kabelresistans
X kabler }            % Kabelinduktans
{max}                   % maks eller min
{N+T,min}            % Net og trafo navn
{w1}                      % Kabelnavn
%
%
%{ R net + trafo | X net + trafo | R kabler | X kabler }{maks/min | net-trafo-navn | kabel-navn}
% impedanser i milliohm
\end{LV-Ik1f-kA}






\begin{LV-ZtilIk1f-min}
{ Rnet 
| Xnet 
| Rtrafo 
| Xtrafo 
|Rkab1 
| Xkab1 
| Rkab2 
| Xkab2 
| Rkab3 
| Xkab3 }
{Ik,navn 
| netnavn 
| trafonavn 
| kabel1navn 
| kabel2navn 
| kabel3navn}
%{ Rnet | Xnet | Rtrafo | Xtrafo | Rkab1 | Xkab1 | Rkab2 | Xkab2 | Rkab3 | Xkab3 }{Ik,navn | netnavn | trafonavn | kabel1navn | kabel2navn | kabel3navn}
\end{LV-ZtilIk1f-min}

## Ztotal-maks
\begin{LV-Ztotal-max}
{ R1 | X1 | R2 | X2 | R3 | X3 | R4 | X4 | R5 | X5 }{Z resultat navn}{Z1 navn | Z2 navn | Z3 navn | Z4 navn | Z5 navn}{Antal_kab 1 | Antal kabler 2 | Antal kabler 3 | Antal kabler 4 | Antal kabler 5}
%{ R1 | X1 | R2 | X2 | R3 | X3 | R4 | X4 | R5 | X5 }{Z resultat navn}{Z1 navn | Z2 navn | Z3 navn | Z4 navn | Z5 navn}{Antal_kab 1 | Antal kabler 2 | Antal kabler 3 | Antal kabler 4 | Antal kabler 5}
\end{LV-Ztotal-max}

## Impedans fra kortslutningsniveau

# Forsyning
## Spændingsfald
\begin{HV-deltaUnet}
	{}                       %{Ib}
	{}                       %{R}
	{}                       %{X}
	{}                       %{cosPhi}
	{}                       %{U navn 
{}                       % | Ib navn}
\end{HV-deltaUnet}

## Ik2f-HV
\begin{HV-ZtilIk2f}{10000}{ 0,45 | 2,67 | 0,47 | 0,19 | 0 | 0 | 0 | 0 | 0 | 0 }{Ik2f,T0,min | NT,max | kabel,Wtot | Z3 navn | Z4 navn | Z5 navn}
%{Un}{ R1 | X1 | R2 | X2 | R3 | X3 | R4 | X4 | R5 | X5 }{Ik,navn | Z1 navn | Z2 navn | Z3 navn | Z4 navn | Z5 navn}
\end{HV-ZtilIk2f}


## 1f-kortslutning-henført
>>>>>>> malthe
\begin{HV-ZtilIk1-prim}
	{10000}{ R1 | X1 | R2 | X2 | R3 | X3 }{Ik,navn | Z1 navn | Z2 navn | Z3 navn}
	%{Un} formlen bruges kun ved el-anlæg, så Un=10000
	%{ Rnet | Xnet | Rkabel | Xkabel | Rtrafo | Xtrafo } 
	%{Ik,navn | Znet navn | Zkabel navn | Ztrafo navn}
\end{HV-ZtilIk1-prim}

## S-jordskinne-trafo
begin{S-skinnejord-trafo}
{}       %{Ik}
{}       %{udløsningstid}
{}       %{start temp}
{}       % {1/2 = relæ/sikring}
{}       % {Ik,navn}
{}        % {tid navn}
{}        %{tværsnit navn}
\end{S-skinnejord-trafo}


## Kortslutning
\begin{ZtilIkHV}
{}                                    %{Rnet}
{}                                    %{Xnet}
{}                                    %{Rkab}
{}                                    %{Xkab}
{}                                    %{Rtra}
{}                                     %{Xtra}
{10000}                         %{Un}
{1fk,                               % k1f, k2f eller k3f
1fk,                                 % strømnav
net,                                 %Navn på første dvs. netimpedans
t,                                      % navn på trafo
w}                                     % navn på kabel
\end{ZtilIkHV}








