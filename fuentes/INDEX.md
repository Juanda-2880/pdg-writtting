# Índice de fuentes

Mapa de cada entrada de [`../thesis/references.bib`](../thesis/references.bib) al PDF que realmente se leyó. Las reglas de uso están en [`README.md`](./README.md).

- **PDF:** ruta local en `pdf/`, con el nombre de la clave BibTeX. Los PDF **no se suben a git** (ver `README.md`), así que un clon nuevo verá *falta* en los enlaces aunque la fila diga que existe: se obtiene por la ruta indicada y se compara con el SHA-256 de abajo.
- **Versión del PDF:** si es la versión publicada, un preprint o una versión de autor. Una cita textual se comprueba siempre contra la versión publicada.
- **Verificada:** si la entrada ya tiene usos comprobados en [`../thesis/CITAS-VERIFICADAS.md`](../thesis/CITAS-VERIFICADAS.md). «sí (parcial)» significa que hay usos verificados, no que todos lo estén.

Actualizado: 2026-09-13 (integración del Marco teórico de JDLP, que añade Burns et al. 2016 y Xu et al. 2024).

## Citadas en la tesis (38)

| Clave BibTeX | Año | Citada en | Referencia | PDF | Versión del PDF | Cómo obtenerla | Verificada |
| :--- | :---: | :--- | :--- | :--- | :--- | :--- | :---: |
| `sculley-hiddentechnicaldebt-2015` | 2015 | cap. 01, cap. 05 | [URL](https://papers.nips.cc/paper/5656-hidden-technical-debt-in-machine-learning-systems) | [`pdf/sculley-hiddentechnicaldebt-2015.pdf`](./pdf/sculley-hiddentechnicaldebt-2015.pdf) | Publicada (actas NeurIPS 2015) | Acceso abierto: papers.nips.cc | sí (parcial) |
| `kreuzberger-mlopsoverview-2023` | 2023 | cap. 01, cap. 05 | [DOI](https://doi.org/10.1109/ACCESS.2023.3262138) | [`pdf/kreuzberger-mlopsoverview-2023.pdf`](./pdf/kreuzberger-mlopsoverview-2023.pdf) | **Preprint** arXiv 2205.02302, no la versión de *IEEE Access* que cita el `.bib` | Acceso abierto: arXiv. Falta la versión publicada | sí (parcial) |
| `eken-mlopsmultivocalreview-2026` | 2026 | cap. 01 | [DOI](https://doi.org/10.1145/3747346) | [`pdf/eken-mlopsmultivocalreview-2026.pdf`](./pdf/eken-mlopsmultivocalreview-2026.pdf) | **Preprint** arXiv 2406.09737v2 (2025-04-16); el resumen citado coincide con el publicado (Crossref) | Acceso abierto: arXiv. Versión publicada en ACM DL | sí (parcial) |
| `lima-mlopspractices-2022` | 2022 | cap. 05 | [DOI](https://doi.org/10.5220/0010997300003179) | [`pdf/lima-mlopspractices-2022.pdf`](./pdf/lima-mlopspractices-2022.pdf) | Publicada (SciTePress, pp. 308–320) | Acceso abierto: scitepress.org | no (su uso del cap. 01 se retiró) |
| `weng-mlaasinthewild-2022` | 2022 | cap. 05 | [URL](https://www.usenix.org/conference/nsdi22/presentation/weng) | [`pdf/weng-mlaasinthewild-2022.pdf`](./pdf/weng-mlaasinthewild-2022.pdf) | Publicada (actas USENIX NSDI 2022) | Acceso abierto: usenix.org | sí (parcial) |
| `gao-lowgpuutilization-2024` | 2024 | cap. 01 | [DOI](https://doi.org/10.1145/3597503.3639232) | [`pdf/gao-lowgpuutilization-2024.pdf`](./pdf/gao-lowgpuutilization-2024.pdf) | Versión de autor (Microsoft Research), no la de ACM | Acceso abierto: microsoft.com/research. Versión publicada en ACM DL | sí (parcial) |
| `liu-gpufailureprediction-2022` | 2022 | cap. 05, cap. 07 | [URL](https://arxiv.org/abs/2201.11853) | [`pdf/liu-gpufailureprediction-2022.pdf`](./pdf/liu-gpufailureprediction-2022.pdf) | **Preprint** arXiv 2201.11853v1, igual que cita el `.bib` | Acceso abierto: arXiv | sí (parcial) |
| `mahajan-themis-2020` | 2020 | cap. 05 | [URL](https://www.usenix.org/conference/nsdi20/presentation/mahajan) | **falta** | — | Acceso abierto: usenix.org | no |
| `narayanan-gavel-2020` | 2020 | cap. 05 | [URL](https://www.usenix.org/conference/osdi20/presentation/narayanan-deepak) | **falta** | — | Acceso abierto: usenix.org | no |
| `qiao-pollux-2021` | 2021 | cap. 05 | [URL](https://www.usenix.org/conference/osdi21/presentation/qiao) | **falta** | — | Acceso abierto: usenix.org | no |
| `verma-borg-2015` | 2015 | cap. 05 | [DOI](https://doi.org/10.1145/2741948.2741964) | **falta** | — | ACM Digital Library (portal Icesi) | no |
| `kwon-pagedattention-2023` | 2023 | cap. 05 | [DOI](https://doi.org/10.1145/3600006.3613165) | **falta** | — | ACM Digital Library (portal Icesi) | no |
| `yu-orca-2022` | 2022 | cap. 05 | [URL](https://www.usenix.org/conference/osdi22/presentation/yu) | **falta** | — | Acceso abierto: usenix.org | no |
| `frantar-gptq-2023` | 2023 | cap. 05 | [URL](https://arxiv.org/abs/2210.17323) | [`pdf/frantar-gptq-2023.pdf`](./pdf/frantar-gptq-2023.pdf) | **Preprint** arXiv 2210.17323v2, marcado como publicado en ICLR 2023 | Acceso abierto: arXiv | parcial (uso del cap. 01 retirado; cap. 05 sin verificar) |
| `lin-awq-2024` | 2024 | cap. 05 | [URL](https://proceedings.mlsys.org/paper_files/paper/2024/hash/42a452cbafa9dd64e9ba4aa95cc1ef21-Abstract-Conference.html) | [`pdf/lin-awq-2024.pdf`](./pdf/lin-awq-2024.pdf) | Publicada (actas MLSys 2024) | Acceso abierto: proceedings.mlsys.org | parcial (uso del cap. 01 retirado; cap. 05 sin verificar) |
| `dettmers-llmint8-2022` | 2022 | cap. 05 | [URL](https://proceedings.neurips.cc/paper_files/paper/2022/hash/c3ba4962c05c49636d4c6206a97e9c8a-Abstract-Conference.html) | [`pdf/dettmers-llmint8-2022.pdf`](./pdf/dettmers-llmint8-2022.pdf) | Publicada (actas NeurIPS 2022) | Acceso abierto: proceedings.neurips.cc | parcial (uso del cap. 01 retirado; cap. 05 sin verificar) |
| `schwaber-scrumguide-2020` | 2020 | cap. 07 | [URL](https://scrumguides.org/docs/scrumguide/v2020/2020-Scrum-Guide-US.pdf) | **falta** | — | Acceso abierto: scrumguides.org | no |
| `jiang-loadtestingsurvey-2015` | 2015 | cap. 05, cap. 07 | [DOI](https://doi.org/10.1109/TSE.2015.2445340) | **falta** | — | Por determinar | no |
| `moritz-ray-2018` | 2018 | cap. 05 | [URL](https://www.usenix.org/conference/osdi18/presentation/moritz) | **falta** | — | Acceso abierto: usenix.org | no |
| `muiruri-mlinferenceserving-2026` | 2026 | cap. 05 | [DOI](https://doi.org/10.1002/spe.70069) | **falta** | — | Por determinar | no |
| `carrion-k8sbibliometric-2022` | 2022 | cap. 05 | [DOI](https://doi.org/10.1007/s10723-022-09629-8) | **falta** | — | Por determinar | no |
| `shamim-k8smultivocal-2022` | 2022 | cap. 05 | [URL](https://arxiv.org/abs/2211.07032) | **falta** | — | Acceso abierto: arXiv | no |
| `miao-llmservingsurvey-2025` | 2025 | cap. 05 | [DOI](https://doi.org/10.1145/3754448) | **falta** | — | ACM Digital Library (portal Icesi) | no |
| `burns-borgomegak8s-2016` | 2016 | cap. 05 | [DOI](https://doi.org/10.1145/2898442.2898444) | **falta** | — | ACM Digital Library (portal Icesi); *ACM Queue* también la publica en acceso abierto | no |
| `xu-k8soperatorbugs-2024` | 2024 | cap. 05 | [DOI](https://doi.org/10.1145/3650212.3680396) | **falta** | — | ACM Digital Library (portal Icesi) | no |
| `weitzel-nrpreservation-2025` | 2025 | cap. 01, cap. 05 | [URL](https://arxiv.org/abs/2505.22864) | [`pdf/weitzel-nrpreservation-2025.pdf`](./pdf/weitzel-nrpreservation-2025.pdf) | **Preprint** arXiv 2505.22864v1 con referencia de PEARC '25 | Acceso abierto: arXiv. Versión publicada en ACM DL (portal Icesi) | sí (parcial) |
| `gao-dlschedulingtaxonomy-2022` | 2022 | cap. 05 | [URL](https://arxiv.org/abs/2205.11913) | **falta** | — | Acceso abierto: arXiv | no |
| `cohen-cloudovercommit-2019` | 2019 | cap. 05 | [DOI](https://doi.org/10.1287/mnsc.2018.3091) | **falta** | — | Por determinar | no |
| `bashir-peakovercommit-2021` | 2021 | cap. 05 | [DOI](https://doi.org/10.1145/3447786.3456259) | **falta** | — | ACM Digital Library (portal Icesi) | no |
| `li-observabilitysurvey-2021` | 2021 | cap. 05 | [DOI](https://doi.org/10.1007/s10664-021-10063-9) | **falta** | — | Por determinar | no |
| `li-rbaccloudsurvey-2015` | 2015 | cap. 05 | [DOI](https://doi.org/10.1007/978-3-319-11104-9_95) | **falta** | — | Por determinar | no |
| `fett-oauth2security-2016` | 2016 | cap. 05 | [DOI](https://doi.org/10.1145/2976749.2978385) | **falta** | — | ACM Digital Library (portal Icesi) | no |
| `montesi-apigatewaypatterns-2016` | 2016 | cap. 05 | [URL](https://arxiv.org/abs/1609.05830) | **falta** | — | Acceso abierto: arXiv | no |
| `lewis-susbenchmarks-2018` | 2018 | cap. 05, cap. 07 | — | **falta** | — | Por determinar | no |
| `chen-llmquantizationsurvey-2026` | 2026 | cap. 05 | [DOI](https://doi.org/10.1007/s11390-026-5979-1) | **falta** | — | Por determinar | no |
| `sevilla-computetrends-2022` | 2022 | cap. 01 | [DOI](https://doi.org/10.1109/IJCNN55064.2022.9891914) | [`pdf/sevilla-computetrends-2022.pdf`](./pdf/sevilla-computetrends-2022.pdf) | **Preprint** arXiv 2202.05924v2, no la versión de IJCNN que cita el `.bib` | Acceso abierto: arXiv. Versión publicada en IEEE Xplore | sí (parcial) |
| `ahmed-industryinfluence-2023` | 2023 | cap. 01 | [DOI](https://doi.org/10.1126/science.ade2420) | [`pdf/ahmed-industryinfluence-2023.pdf`](./pdf/ahmed-industryinfluence-2023.pdf) | Copia del MIT IDE con la maquetación de *Science*, previa a la impresión final | Acceso abierto: ide.mit.edu. Versión publicada en *Science* (no está en los portales listados) | sí (parcial) |
| `xu-sing-2025` | 2025 | cap. 01 | [DOI](https://doi.org/10.1145/3669940.3707266) | [`pdf/xu-sing-2025.pdf`](./pdf/xu-sing-2025.pdf) | **Preprint** arXiv 2110.01556v2 con encabezado de ASPLOS '25 | Acceso abierto: arXiv. Versión publicada en ACM DL (portal Icesi) | sí (parcial) |

## En `references.bib` pero sin citar (8)

No hace falta conseguir estos PDF mientras no se citen. Dos son anteriores a 2015 y no pueden citarse (`../skills/reference-writting/recency.md`). `jeon-philly-2019` y `gu-tiresias-2019` salieron del cap. 01 el 2026-09-13 y quedan como candidatos para el Estado del arte. `wiest-privacypreservingllm-2024` salió de la Justificación el 2026-09-13.

| Clave BibTeX | Año | Citada en | Referencia | PDF | Versión del PDF | Cómo obtenerla | Verificada |
| :--- | :---: | :--- | :--- | :--- | :--- | :--- | :---: |
| `wiest-privacypreservingllm-2024` | 2024 | — | [DOI](https://doi.org/10.1038/s41746-024-01233-2) | [`pdf/wiest-privacypreservingllm-2024.pdf`](./pdf/wiest-privacypreservingllm-2024.pdf) | Publicada (*npj Digital Medicine*) | Acceso abierto: nature.com | pasajes verificados; uso retirado |
| `jeon-philly-2019` | 2019 | — | [URL](https://www.usenix.org/conference/atc19/presentation/jeon) | [`pdf/jeon-philly-2019.pdf`](./pdf/jeon-philly-2019.pdf) | Publicada (actas USENIX ATC 2019) | Acceso abierto: usenix.org | no (usos del cap. 01 retirados; candidatos para el Estado del arte) |
| `gu-tiresias-2019` | 2019 | — | [URL](https://www.usenix.org/conference/nsdi19/presentation/gu) | [`pdf/gu-tiresias-2019.pdf`](./pdf/gu-tiresias-2019.pdf) | Publicada (actas USENIX NSDI 2019) | Acceso abierto: usenix.org | no (usos del cap. 01 retirados; candidatos para el Estado del arte) |
| `xiao-gandiva-2018` | 2018 | — | [URL](https://www.usenix.org/conference/osdi18/presentation/xiao) | **falta** | — | Acceso abierto: usenix.org | no |
| `cortez-resourcecentral-2017` | 2017 | — | [DOI](https://doi.org/10.1145/3132747.3132772) | **falta** | — | ACM Digital Library (portal Icesi) | no |
| `vavilapalli-yarn-2013` | 2013 | — | [DOI](https://doi.org/10.1145/2523616.2523633) | **falta** | — | ACM Digital Library (portal Icesi) | no |
| `yoo-slurm-2003` | 2003 | — | [DOI](https://doi.org/10.1007/10968987_3) | **falta** | — | Por determinar | no |
| `george-hpcgpuclassroom-2020` | 2020 | — | [URL](https://arxiv.org/abs/2005.07598) | [`pdf/george-hpcgpuclassroom-2020.pdf`](./pdf/george-hpcgpuclassroom-2020.pdf) | **Preprint** arXiv 2005.07598v1 (informe, sin revisión por pares) | Acceso abierto: arXiv | no |

## Pendientes de descarga manual

Fuentes que un agente no pudo descargar porque el portal pide la cuenta de la universidad o bloquea clientes automáticos. Una persona las descarga y deja el archivo en `pdf/<clave>.pdf`.

| Clave BibTeX | Qué falta | Dónde |
| :--- | :--- | :--- |
| `eken-mlopsmultivocalreview-2026` | Versión publicada | sí (parcial) |
| `gao-lowgpuutilization-2024` | Versión publicada | [ACM DL, doi:10.1145/3597503.3639232](https://doi.org/10.1145/3597503.3639232) (el agente recibió HTTP 403) |
| `kreuzberger-mlopsoverview-2023` | Versión publicada | [IEEE Access, doi:10.1109/ACCESS.2023.3262138](https://doi.org/10.1109/ACCESS.2023.3262138) (revista de acceso abierto; IEEE Xplore no está entre los portales listados) |

## Huellas SHA-256 de los PDF locales

Para comprobar que el archivo de otro autor es el mismo que se verificó: `sha256sum fuentes/pdf/<clave>.pdf`.

| Archivo | SHA-256 |
| :--- | :--- |
| `sculley-hiddentechnicaldebt-2015.pdf` | `1a67da09a8bd5ba9a3577176e30aa2fbd88534e6baf0bc31522b4999f643d2a1` |
| `kreuzberger-mlopsoverview-2023.pdf` | `680907b6ee15a9ca113c33acfc981988dc6dc7fcf06c337a2e112dd5d7aff319` |
| `lima-mlopspractices-2022.pdf` | `fc686dd9c238f9be3e6e985e9e7a46376061930dd1172ad1e703d446725d80be` |
| `gao-lowgpuutilization-2024.pdf` | `84f075ff5f1ddffb46498d830d0ce9e9be15c8aa304ec857818a75129db34bdb` |
| `eken-mlopsmultivocalreview-2026.pdf` | `b67b11c977f032658881ab4e889b20fe5c4de33e637af1900ac43dc4b7a80f5a` |
| `jeon-philly-2019.pdf` | `a8eeef03a92ecb96b737ee3a9689d75e82865f9a77f0397042eb0693d5645b44` |
| `gu-tiresias-2019.pdf` | `09cda6426c5130f7df1386953640bd4d513f4946c0c7bf178d9219adca71e245` |
| `weng-mlaasinthewild-2022.pdf` | `4fa944ce9d6dd6e9daf66fe68a03538dc3fb50ed947b59f2a196e4eb26c6e895` |
| `liu-gpufailureprediction-2022.pdf` | `8dc3b1068ad178e0dccd4c5cb0406cde446aec44b5ce04b847a79a257f8ef968` |
| `sevilla-computetrends-2022.pdf` | `e9fa16ea47877d43981541d946ec5a1fb35e8aea5dd60e4389beed254eb375ae` |
| `ahmed-industryinfluence-2023.pdf` | `69986c7032541c4d5803a29cc401efc37fc45e83a42969058f8c996d8f42e74c` |
| `xu-sing-2025.pdf` | `213a59c0489bfa986e249a6b9f54888f9198a830b4e1a1689990a8eb72fdb82c` |
| `weitzel-nrpreservation-2025.pdf` | `42c33ae0b8619e1f4cdaf1556ef8826ae125328513d581f55ef821468f0253a1` |
| `george-hpcgpuclassroom-2020.pdf` | `2084864b166a335a311563d24a82d06e05b93d94d10b7f823f7809ca192d517f` |
| `frantar-gptq-2023.pdf` | `35e339171cd48bbf8dda246bd018b11aa33a5cda0c4a1587cdae574208f56396` |
| `lin-awq-2024.pdf` | `cd7b88325267627b7159dfc32d3ee3fc5430718bd722afee6da25e14ff7525d6` |
| `dettmers-llmint8-2022.pdf` | `a7de7700cb8d0a36eb1c7926add3ec10530f53be8d81c681e7de372586d58f77` |
| `wiest-privacypreservingllm-2024.pdf` | `32d21c85ee31c11d5b50752d690a6d6ca499187fa609e00d6fd1ee86aa73d97e` |
