# Índice de fuentes

Mapa de cada entrada de [`../thesis/references.bib`](../thesis/references.bib) al PDF que realmente se leyó. Las reglas de uso están en [`README.md`](./README.md).

- **PDF:** ruta local en `pdf/`, con el nombre de la clave BibTeX. Los PDF **no se suben a git** (ver `README.md`), así que un clon nuevo verá *falta* en los enlaces aunque la fila diga que existe: se obtiene por la ruta indicada y se compara con el SHA-256 de abajo.
- **Versión del PDF:** si es la versión publicada, un preprint o una versión de autor. Una cita textual se comprueba siempre contra la versión publicada.
- **Verificada:** si la entrada ya tiene usos comprobados en [`../thesis/CITAS-VERIFICADAS.md`](../thesis/CITAS-VERIFICADAS.md). «sí (parcial)» significa que hay usos verificados, no que todos lo estén.

Actualizado: 2026-10-04 (cap. 06: cinco páginas de documentación oficial añadidas, 47 citadas); anterior: 2026-09-27 (revisión completa del documento: 26 fuentes nuevas en `pdf/`, verificación de los caps. 05, 06 y 07). El mismo día salió `lewis-susbenchmarks-2018` de `references.bib`, junto con el *System Usability Scale* del objetivo 4.

## Citadas en la tesis (47)

| Clave BibTeX | Año | Citada en | Referencia | PDF | Versión del PDF | Cómo obtenerla | Verificada |
| :--- | :---: | :--- | :--- | :--- | :--- | :--- | :---: |
| `sculley-hiddentechnicaldebt-2015` | 2015 | cap. 01, cap. 05, cap. 06 | [URL](https://papers.nips.cc/paper/5656-hidden-technical-debt-in-machine-learning-systems) | [`pdf/sculley-hiddentechnicaldebt-2015.pdf`](./pdf/sculley-hiddentechnicaldebt-2015.pdf) | Publicada (actas NeurIPS 2015) | Acceso abierto: papers.nips.cc | sí |
| `kreuzberger-mlopsoverview-2023` | 2023 | cap. 01, cap. 05, cap. 06 | [DOI](https://doi.org/10.1109/ACCESS.2023.3262138) | [`pdf/kreuzberger-mlopsoverview-2023.pdf`](./pdf/kreuzberger-mlopsoverview-2023.pdf) | **Preprint** arXiv 2205.02302, no la versión de *IEEE Access* que cita el `.bib` | Acceso abierto: arXiv. Falta la versión publicada | sí |
| `eken-mlopsmultivocalreview-2026` | 2026 | cap. 01, cap. 06 | [DOI](https://doi.org/10.1145/3747346) | [`pdf/eken-mlopsmultivocalreview-2026.pdf`](./pdf/eken-mlopsmultivocalreview-2026.pdf) | **Preprint** arXiv 2406.09737v2 (2025-04-16); el resumen citado coincide con el publicado (Crossref) | Acceso abierto: arXiv. Versión publicada en ACM DL | sí (parcial) |
| `lima-mlopspractices-2022` | 2022 | cap. 05 | [DOI](https://doi.org/10.5220/0010997300003179) | [`pdf/lima-mlopspractices-2022.pdf`](./pdf/lima-mlopspractices-2022.pdf) | Publicada (SciTePress, pp. 308–320) | Acceso abierto: scitepress.org | sí |
| `weng-mlaasinthewild-2022` | 2022 | cap. 05, cap. 06 | [URL](https://www.usenix.org/conference/nsdi22/presentation/weng) | [`pdf/weng-mlaasinthewild-2022.pdf`](./pdf/weng-mlaasinthewild-2022.pdf) | Publicada (actas USENIX NSDI 2022) | Acceso abierto: usenix.org | sí |
| `gao-lowgpuutilization-2024` | 2024 | cap. 01, cap. 05, cap. 06 | [DOI](https://doi.org/10.1145/3597503.3639232) | [`pdf/gao-lowgpuutilization-2024.pdf`](./pdf/gao-lowgpuutilization-2024.pdf) | Versión de autor (Microsoft Research), no la de ACM | Acceso abierto: microsoft.com/research. Versión publicada en ACM DL | sí |
| `liu-gpufailureprediction-2022` | 2022 | cap. 05 | [URL](https://arxiv.org/abs/2201.11853) | [`pdf/liu-gpufailureprediction-2022.pdf`](./pdf/liu-gpufailureprediction-2022.pdf) | **Preprint** arXiv 2201.11853v1, igual que cita el `.bib` | Acceso abierto: arXiv | sí |
| `mahajan-themis-2020` | 2020 | cap. 05, cap. 06 | [URL](https://www.usenix.org/conference/nsdi20/presentation/mahajan) | [`pdf/mahajan-themis-2020.pdf`](./pdf/mahajan-themis-2020.pdf) | Publicada (actas USENIX NSDI 2020) | Acceso abierto: usenix.org | sí |
| `narayanan-gavel-2020` | 2020 | cap. 05, cap. 06 | [URL](https://www.usenix.org/conference/osdi20/presentation/narayanan-deepak) | [`pdf/narayanan-gavel-2020.pdf`](./pdf/narayanan-gavel-2020.pdf) | Publicada (actas USENIX OSDI 2020) | Acceso abierto: usenix.org | sí |
| `qiao-pollux-2021` | 2021 | cap. 05 | [URL](https://www.usenix.org/conference/osdi21/presentation/qiao) | [`pdf/qiao-pollux-2021.pdf`](./pdf/qiao-pollux-2021.pdf) | Publicada (actas USENIX OSDI 2021) | Acceso abierto: usenix.org | sí |
| `verma-borg-2015` | 2015 | cap. 05 | [DOI](https://doi.org/10.1145/2741948.2741964) | [`pdf/verma-borg-2015.pdf`](./pdf/verma-borg-2015.pdf) | Versión de Google Research del artículo de EuroSys '15 | ACM Digital Library (portal Icesi) | sí |
| `kwon-pagedattention-2023` | 2023 | cap. 05, cap. 06 | [DOI](https://doi.org/10.1145/3600006.3613165) | [`pdf/kwon-pagedattention-2023.pdf`](./pdf/kwon-pagedattention-2023.pdf) | **Preprint** arXiv 2309.06180, no la versión de SOSP '23 | ACM Digital Library (portal Icesi) | sí |
| `yu-orca-2022` | 2022 | cap. 05, cap. 06 | [URL](https://www.usenix.org/conference/osdi22/presentation/yu) | [`pdf/yu-orca-2022.pdf`](./pdf/yu-orca-2022.pdf) | Publicada (actas USENIX OSDI 2022) | Acceso abierto: usenix.org | sí |
| `frantar-gptq-2023` | 2023 | cap. 05, cap. 06 | [URL](https://arxiv.org/abs/2210.17323) | [`pdf/frantar-gptq-2023.pdf`](./pdf/frantar-gptq-2023.pdf) | **Preprint** arXiv 2210.17323v2, marcado como publicado en ICLR 2023 | Acceso abierto: arXiv | sí |
| `lin-awq-2024` | 2024 | cap. 05 | [URL](https://proceedings.mlsys.org/paper_files/paper/2024/hash/42a452cbafa9dd64e9ba4aa95cc1ef21-Abstract-Conference.html) | [`pdf/lin-awq-2024.pdf`](./pdf/lin-awq-2024.pdf) | Publicada (actas MLSys 2024) | Acceso abierto: proceedings.mlsys.org | sí |
| `dettmers-llmint8-2022` | 2022 | cap. 05 | [URL](https://proceedings.neurips.cc/paper_files/paper/2022/hash/c3ba4962c05c49636d4c6206a97e9c8a-Abstract-Conference.html) | [`pdf/dettmers-llmint8-2022.pdf`](./pdf/dettmers-llmint8-2022.pdf) | Publicada (actas NeurIPS 2022) | Acceso abierto: proceedings.neurips.cc | sí |
| `schwaber-scrumguide-2020` | 2020 | cap. 07 | [URL](https://scrumguides.org/docs/scrumguide/v2020/2020-Scrum-Guide-US.pdf) | [`pdf/schwaber-scrumguide-2020.pdf`](./pdf/schwaber-scrumguide-2020.pdf) | Publicada (scrumguides.org) | Acceso abierto: scrumguides.org | sí |
| `jiang-loadtestingsurvey-2015` | 2015 | cap. 05 | [DOI](https://doi.org/10.1109/TSE.2015.2445340) | [`pdf/jiang-loadtestingsurvey-2015.pdf`](./pdf/jiang-loadtestingsurvey-2015.pdf) | Versión de autor con la maquetación de IEEE TSE | Por determinar | sí |
| `moritz-ray-2018` | 2018 | cap. 05 | [URL](https://www.usenix.org/conference/osdi18/presentation/moritz) | [`pdf/moritz-ray-2018.pdf`](./pdf/moritz-ray-2018.pdf) | Publicada (actas USENIX OSDI 2018) | Acceso abierto: usenix.org | sí |
| `muiruri-mlinferenceserving-2026` | 2026 | cap. 06 | [DOI](https://doi.org/10.1002/spe.70069) | [`pdf/muiruri-mlinferenceserving-2026.pdf`](./pdf/muiruri-mlinferenceserving-2026.pdf) | Publicada (*Software: Practice and Experience*, acceso abierto), descargada por los autores | Por determinar | no |
| `carrion-k8sbibliometric-2022` | 2022 | cap. 05 | [DOI](https://doi.org/10.1007/s10723-022-09629-8) | [`pdf/carrion-k8sbibliometric-2022.pdf`](./pdf/carrion-k8sbibliometric-2022.pdf) | Publicada (*Journal of Grid Computing*), descargada por los autores | Por determinar | sí |
| `shamim-k8smultivocal-2022` | 2022 | cap. 05 | [URL](https://arxiv.org/abs/2211.07032) | [`pdf/shamim-k8smultivocal-2022.pdf`](./pdf/shamim-k8smultivocal-2022.pdf) | **Preprint** arXiv 2211.07032 (manuscrito para *Empirical Software Engineering*) | Acceso abierto: arXiv | sí |
| `miao-llmservingsurvey-2025` | 2025 | cap. 05, cap. 06 | [DOI](https://doi.org/10.1145/3754448) | [`pdf/miao-llmservingsurvey-2025.pdf`](./pdf/miao-llmservingsurvey-2025.pdf) | **Preprint** arXiv 2312.15234 (enviado a *ACM Computing Surveys*) | ACM Digital Library (portal Icesi) | sí |
| `burns-borgomegak8s-2016` | 2016 | cap. 05 | [DOI](https://doi.org/10.1145/2898442.2898444) | [`pdf/burns-borgomegak8s-2016.pdf`](./pdf/burns-borgomegak8s-2016.pdf) | Versión de *ACM Queue* en acceso abierto (Google Research) | ACM Digital Library (portal Icesi); *ACM Queue* también la publica en acceso abierto | sí |
| `xu-k8soperatorbugs-2024` | 2024 | cap. 05 | [DOI](https://doi.org/10.1145/3650212.3680396) | [`pdf/xu-k8soperatorbugs-2024.pdf`](./pdf/xu-k8soperatorbugs-2024.pdf) | Publicada (actas ISSTA '24, CC BY 4.0) | ACM Digital Library (portal Icesi) | sí |
| `weitzel-nrpreservation-2025` | 2025 | cap. 05, cap. 06 | [URL](https://arxiv.org/abs/2505.22864) | [`pdf/weitzel-nrpreservation-2025.pdf`](./pdf/weitzel-nrpreservation-2025.pdf) | **Preprint** arXiv 2505.22864v1 con referencia de PEARC '25 | Acceso abierto: arXiv. Versión publicada en ACM DL (portal Icesi) | sí |
| `gao-dlschedulingtaxonomy-2022` | 2022 | cap. 05 | [URL](https://arxiv.org/abs/2205.11913) | [`pdf/gao-dlschedulingtaxonomy-2022.pdf`](./pdf/gao-dlschedulingtaxonomy-2022.pdf) | **Preprint** arXiv 2205.11913v3; publicado después en *ACM Computing Surveys* (2024) con otro título | Acceso abierto: arXiv | sí |
| `cohen-cloudovercommit-2019` | 2019 | cap. 05 | [DOI](https://doi.org/10.1287/mnsc.2018.3091) | [`pdf/cohen-cloudovercommit-2019.pdf`](./pdf/cohen-cloudovercommit-2019.pdf) | Versión de autor con la maquetación de *Management Science* | Por determinar | sí |
| `bashir-peakovercommit-2021` | 2021 | cap. 05 | [DOI](https://doi.org/10.1145/3447786.3456259) | [`pdf/bashir-peakovercommit-2021.pdf`](./pdf/bashir-peakovercommit-2021.pdf) | Versión de autor (noman-bashir.github.io) | ACM Digital Library (portal Icesi) | sí |
| `li-observabilitysurvey-2021` | 2021 | cap. 05 | [DOI](https://doi.org/10.1007/s10664-021-10063-9) | [`pdf/li-observabilitysurvey-2021.xml`](./pdf/li-observabilitysurvey-2021.xml) | Publicada; texto completo XML de Europe PMC (PMC8629732), sin paginación | Por determinar | sí |
| `li-rbaccloudsurvey-2015` | 2015 | cap. 05 | [DOI](https://doi.org/10.1007/978-3-319-11104-9_95) | [`pdf/li-rbaccloudsurvey-2015.pdf`](./pdf/li-rbaccloudsurvey-2015.pdf) | Publicada (Springer, CENet 2014), descargada por los autores | Por determinar | sí |
| `fett-oauth2security-2016` | 2016 | cap. 05 | [DOI](https://doi.org/10.1145/2976749.2978385) | [`pdf/fett-oauth2security-2016.pdf`](./pdf/fett-oauth2security-2016.pdf) | Versión extendida arXiv 1601.01229v4 (la de CCS '16 es abreviada) | ACM Digital Library (portal Icesi) | sí |
| `montesi-apigatewaypatterns-2016` | 2016 | cap. 05, cap. 06 | [URL](https://arxiv.org/abs/1609.05830) | [`pdf/montesi-apigatewaypatterns-2016.pdf`](./pdf/montesi-apigatewaypatterns-2016.pdf) | **Preprint** arXiv 1609.05830 | Acceso abierto: arXiv | sí |
| `chen-llmquantizationsurvey-2026` | 2026 | cap. 05, cap. 06 | [DOI](https://doi.org/10.1007/s11390-026-5979-1) | [`pdf/chen-llmquantizationsurvey-2026.pdf`](./pdf/chen-llmquantizationsurvey-2026.pdf) | Publicada (*JCST*), descargada por los autores | Por determinar | sí |
| `sevilla-computetrends-2022` | 2022 | cap. 01 | [DOI](https://doi.org/10.1109/IJCNN55064.2022.9891914) | [`pdf/sevilla-computetrends-2022.pdf`](./pdf/sevilla-computetrends-2022.pdf) | **Preprint** arXiv 2202.05924v2, no la versión de IJCNN que cita el `.bib` | Acceso abierto: arXiv. Versión publicada en IEEE Xplore | sí |
| `ahmed-industryinfluence-2023` | 2023 | cap. 01 | [DOI](https://doi.org/10.1126/science.ade2420) | [`pdf/ahmed-industryinfluence-2023.pdf`](./pdf/ahmed-industryinfluence-2023.pdf) | Copia del MIT IDE con la maquetación de *Science*, previa a la impresión final | Acceso abierto: ide.mit.edu. Versión publicada en *Science* (no está en los portales listados) | sí |
| `xu-sing-2025` | 2025 | cap. 01, cap. 06 | [DOI](https://doi.org/10.1145/3669940.3707266) | [`pdf/xu-sing-2025.pdf`](./pdf/xu-sing-2025.pdf) | **Preprint** arXiv 2110.01556v2 con encabezado de ASPLOS '25 | Acceso abierto: arXiv. Versión publicada en ACM DL (portal Icesi) | sí |
| `jeon-philly-2019` | 2019 | cap. 05, cap. 06 | [URL](https://www.usenix.org/conference/atc19/presentation/jeon) | [`pdf/jeon-philly-2019.pdf`](./pdf/jeon-philly-2019.pdf) | Publicada (actas USENIX ATC 2019) | Acceso abierto: usenix.org | sí |
| `gu-tiresias-2019` | 2019 | cap. 05, cap. 06 | [URL](https://www.usenix.org/conference/nsdi19/presentation/gu) | [`pdf/gu-tiresias-2019.pdf`](./pdf/gu-tiresias-2019.pdf) | Publicada (actas USENIX NSDI 2019) | Acceso abierto: usenix.org | sí |
| `xiao-gandiva-2018` | 2018 | cap. 05 | [URL](https://www.usenix.org/conference/osdi18/presentation/xiao) | [`pdf/xiao-gandiva-2018.pdf`](./pdf/xiao-gandiva-2018.pdf) | Publicada (actas USENIX OSDI 2018) | Acceso abierto: usenix.org | sí |
| `cortez-resourcecentral-2017` | 2017 | cap. 05 | [DOI](https://doi.org/10.1145/3132747.3132772) | [`pdf/cortez-resourcecentral-2017.pdf`](./pdf/cortez-resourcecentral-2017.pdf) | Versión de Microsoft Research del artículo de SOSP '17 | ACM Digital Library (portal Icesi) | sí |
| `george-hpcgpuclassroom-2020` | 2020 | cap. 05, cap. 06 | [URL](https://arxiv.org/abs/2005.07598) | [`pdf/george-hpcgpuclassroom-2020.pdf`](./pdf/george-hpcgpuclassroom-2020.pdf) | **Preprint** arXiv 2005.07598v1 (informe, sin revisión por pares) | Acceso abierto: arXiv | sí |
| `litellm-overview-2026` | 2026 | cap. 06 | [URL](https://docs.litellm.ai/docs/) | [`pdf/litellm-overview-2026.html`](./pdf/litellm-overview-2026.html) | Página web (documentación oficial), no producción arbitrada | Acceso abierto: docs.litellm.ai | sí |
| `litellm-proxyusers-2026` | 2026 | cap. 06 | [URL](https://docs.litellm.ai/docs/proxy/users) | [`pdf/litellm-proxyusers-2026.html`](./pdf/litellm-proxyusers-2026.html) | Página web (documentación oficial) | Acceso abierto: docs.litellm.ai | sí |
| `kubeflow-profiles-2026` | 2026 | cap. 06 | [URL](https://www.kubeflow.org/docs/components/central-dash/profiles/) | [`pdf/kubeflow-profiles-2026.html`](./pdf/kubeflow-profiles-2026.html) | Página web (documentación oficial) | Acceso abierto: kubeflow.org | sí |
| `slurm-overview-2026` | 2026 | cap. 06 | [URL](https://slurm.schedmd.com/overview.html) | [`pdf/slurm-overview-2026.html`](./pdf/slurm-overview-2026.html) | Página web (documentación oficial) | Acceso abierto: slurm.schedmd.com | sí |
| `llamacpp-readme-2026` | 2026 | cap. 06 | [URL](https://github.com/ggml-org/llama.cpp) | [`pdf/llamacpp-readme-2026.md`](./pdf/llamacpp-readme-2026.md) | Página web (README oficial del repositorio, rama principal) | Acceso abierto: github.com | sí |

## En `references.bib` pero sin citar (3)

No hace falta conseguir estos PDF mientras no se citen. Dos son anteriores a 2015 y no pueden citarse (`../skills/reference-writting/recency.md`). `wiest-privacypreservingllm-2024` salió de la Justificación el 2026-09-13.

| Clave BibTeX | Año | Citada en | Referencia | PDF | Versión del PDF | Cómo obtenerla | Verificada |
| :--- | :---: | :--- | :--- | :--- | :--- | :--- | :---: |
| `wiest-privacypreservingllm-2024` | 2024 | — | [DOI](https://doi.org/10.1038/s41746-024-01233-2) | [`pdf/wiest-privacypreservingllm-2024.pdf`](./pdf/wiest-privacypreservingllm-2024.pdf) | Publicada (*npj Digital Medicine*) | Acceso abierto: nature.com | pasajes verificados; uso retirado |
| `vavilapalli-yarn-2013` | 2013 | — | [DOI](https://doi.org/10.1145/2523616.2523633) | **falta** | — | ACM Digital Library (portal Icesi) | no |
| `yoo-slurm-2003` | 2003 | — | [DOI](https://doi.org/10.1007/10968987_3) | **falta** | — | Por determinar | no |

## Pendientes de descarga manual

Fuentes que un agente no pudo descargar porque el portal pide la cuenta de la universidad o bloquea clientes automáticos. Una persona las descarga y deja el archivo en `pdf/<clave>.pdf`.

| Clave BibTeX | Qué falta | Dónde |
| :--- | :--- | :--- |
| `eken-mlopsmultivocalreview-2026` | Versión publicada | [ACM DL, doi:10.1145/3747346](https://doi.org/10.1145/3747346) (el agente recibió HTTP 403) |
| `gao-lowgpuutilization-2024` | Versión publicada | [ACM DL, doi:10.1145/3597503.3639232](https://doi.org/10.1145/3597503.3639232) (el agente recibió HTTP 403) |
| `kreuzberger-mlopsoverview-2023` | Versión publicada | [IEEE Access, doi:10.1109/ACCESS.2023.3262138](https://doi.org/10.1109/ACCESS.2023.3262138) (revista de acceso abierto; IEEE Xplore no está entre los portales listados) |

## Huellas SHA-256 de los PDF locales

Para comprobar que el archivo de otro autor es el mismo que se verificó: `sha256sum fuentes/pdf/<clave>.pdf`.

| Archivo | SHA-256 |
| :--- | :--- |
| `ahmed-industryinfluence-2023.pdf` | `69986c7032541c4d5803a29cc401efc37fc45e83a42969058f8c996d8f42e74c` |
| `bashir-peakovercommit-2021.pdf` | `33d54b5af9d04ed33b497ae7560060b25428552106de1494ed5a9ab565027e4d` |
| `burns-borgomegak8s-2016.pdf` | `0679da43280d8c3903eb23b1516b92087c3168430ff2a65e70e0e426a86a5a4b` |
| `carrion-k8sbibliometric-2022.pdf` | `9d3653ce3a06e6999e6d07aba0cfad13af49354a7fa6a21cd9646009ea7bb263` |
| `chen-llmquantizationsurvey-2026.pdf` | `27f98dc8f8fe84333efba4e63d1b2a6394b7b0d1ce24c7a1d8971b3c034e72af` |
| `cohen-cloudovercommit-2019.pdf` | `83b76fa36b73a4c4fdc1468e1f474610d99637c27d8f5828caedcca02928acd2` |
| `cortez-resourcecentral-2017.pdf` | `715d2c6b7c844949e4c7fc6d656c9ad5f08129676264706607e087b6605ff9ce` |
| `dettmers-llmint8-2022.pdf` | `a7de7700cb8d0a36eb1c7926add3ec10530f53be8d81c681e7de372586d58f77` |
| `eken-mlopsmultivocalreview-2026.pdf` | `b67b11c977f032658881ab4e889b20fe5c4de33e637af1900ac43dc4b7a80f5a` |
| `fett-oauth2security-2016.pdf` | `153f4c68a3be5cd4f12be91c1882014ecd4579204a40189fba6a9feb4d8ed2f6` |
| `frantar-gptq-2023.pdf` | `35e339171cd48bbf8dda246bd018b11aa33a5cda0c4a1587cdae574208f56396` |
| `gao-dlschedulingtaxonomy-2022.pdf` | `6e78ba0ffa7830392bc6498fd33459cc289ac7c7f0a6176425857a1872fc80b2` |
| `gao-lowgpuutilization-2024.pdf` | `84f075ff5f1ddffb46498d830d0ce9e9be15c8aa304ec857818a75129db34bdb` |
| `george-hpcgpuclassroom-2020.pdf` | `2084864b166a335a311563d24a82d06e05b93d94d10b7f823f7809ca192d517f` |
| `gu-tiresias-2019.pdf` | `09cda6426c5130f7df1386953640bd4d513f4946c0c7bf178d9219adca71e245` |
| `jeon-philly-2019.pdf` | `a8eeef03a92ecb96b737ee3a9689d75e82865f9a77f0397042eb0693d5645b44` |
| `jiang-loadtestingsurvey-2015.pdf` | `b9092f02571b4356455675936c625ec679a036cbff37f890cd5abcbc321ded1b` |
| `kreuzberger-mlopsoverview-2023.pdf` | `680907b6ee15a9ca113c33acfc981988dc6dc7fcf06c337a2e112dd5d7aff319` |
| `kwon-pagedattention-2023.pdf` | `55b3b324d779a67c59dac2519445e3b07c14e6ff5c656fadb47a3d7b5997469e` |
| `li-observabilitysurvey-2021.xml` | `faf5c3de1429ca014be28748626a1ad0ac1fb69e36634b6d7a87d210adf522e6` |
| `li-rbaccloudsurvey-2015.pdf` | `e1e5ef475d1a40f85078b96446a660ef16740cec4347628d39981e8fdd07147b` |
| `lima-mlopspractices-2022.pdf` | `fc686dd9c238f9be3e6e985e9e7a46376061930dd1172ad1e703d446725d80be` |
| `lin-awq-2024.pdf` | `cd7b88325267627b7159dfc32d3ee3fc5430718bd722afee6da25e14ff7525d6` |
| `liu-gpufailureprediction-2022.pdf` | `8dc3b1068ad178e0dccd4c5cb0406cde446aec44b5ce04b847a79a257f8ef968` |
| `mahajan-themis-2020.pdf` | `45f460204a73fc2627fdbc8ee85c79391a2f93715e8b35f806c0c6737d584afa` |
| `miao-llmservingsurvey-2025.pdf` | `a522d1fe410927d135a9447a265072d2bef2e43ee41165a5b7bdda927528c953` |
| `montesi-apigatewaypatterns-2016.pdf` | `d07c7f229da87cf680c00c71259a27b22dbd87aae33e8c22e0ff3085edb1f1a5` |
| `moritz-ray-2018.pdf` | `066fecee9604ca232b5fbaeaa7dd260c88149a1be6dd4357ef16705986b99290` |
| `muiruri-mlinferenceserving-2026.pdf` | `2fdf4e15ab40ecd458c3eca96ea17814d15978bbd1c37b262cc527ae48c15b3e` |
| `narayanan-gavel-2020.pdf` | `14dfd28574f02845542c063e850c2adf2c39ab618fab42845d614d34585dac82` |
| `qiao-pollux-2021.pdf` | `5d19b61a0c5dcb010b71ee0e395f9bffbdae1f50112f685ae12b2fdc0f9a20ad` |
| `schwaber-scrumguide-2020.pdf` | `ed83eb2378459c9e5da5e695844a24c3770fba33687cafaf0a0683ad5070b3ec` |
| `sculley-hiddentechnicaldebt-2015.pdf` | `1a67da09a8bd5ba9a3577176e30aa2fbd88534e6baf0bc31522b4999f643d2a1` |
| `sevilla-computetrends-2022.pdf` | `e9fa16ea47877d43981541d946ec5a1fb35e8aea5dd60e4389beed254eb375ae` |
| `shamim-k8smultivocal-2022.pdf` | `51ca9730277af23275b5e805b72286d51768ba5ba2fa6bba7ab490e54e18e9d7` |
| `verma-borg-2015.pdf` | `2fdacd3b69f8af91477412fc91d1d858a43e764929a4edb646bd517ededdad94` |
| `weitzel-nrpreservation-2025.pdf` | `42c33ae0b8619e1f4cdaf1556ef8826ae125328513d581f55ef821468f0253a1` |
| `weng-mlaasinthewild-2022.pdf` | `4fa944ce9d6dd6e9daf66fe68a03538dc3fb50ed947b59f2a196e4eb26c6e895` |
| `wiest-privacypreservingllm-2024.pdf` | `32d21c85ee31c11d5b50752d690a6d6ca499187fa609e00d6fd1ee86aa73d97e` |
| `xiao-gandiva-2018.pdf` | `1c21bf8c2502284287b364fea02063786d5965b912cbda6d3849da34a566f584` |
| `xu-k8soperatorbugs-2024.pdf` | `def7dad86280b95858743ea9c1d99cc2030ae3aa576e40d8f3db91b7484e2ace` |
| `xu-sing-2025.pdf` | `213a59c0489bfa986e249a6b9f54888f9198a830b4e1a1689990a8eb72fdb82c` |
| `yu-orca-2022.pdf` | `b8038438ad8ff99bb131c1a6e16f7df10cf2f962aeb1bf4f1c00cc37e70658ca` |
| `kubeflow-profiles-2026.html` | `cff218623bb2bbf19e9114a1441158dfe0776624636d7adf91d06dc3ff851b78` |
| `litellm-overview-2026.html` | `f6b924e38c7015efd0984c1a4201661ad3be2d0c12bdf0d50bec64f67f4c2b37` |
| `litellm-proxyusers-2026.html` | `a59d5aefc4e4fc6c084a612e694cfd6c7865e7ba4d698d8494b8b844bf1036ee` |
| `slurm-overview-2026.html` | `95a38035cae196a4ff790022d2125cfabcee618485a415233a345f4144756e93` |
| `llamacpp-readme-2026.md` | `dc2d34687c844ecf929d9e9a9c9c78e8023b52abf3b2b3d039600c79016673b6` |
