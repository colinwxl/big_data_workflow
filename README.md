## 大数据工作流开源系统一览表
<http://www.jdon.com/bigdata/pipeline.html>

以下是各类数据分析的工作流pipeline管道模型的框架和库包，包含特定科学等业务领域行业或者通用领域，结合大数据big data分析的各种开放源码项目。包括下一代测序技术(NGS)打开了数据分析的空间，生物学成为数据密集领域，越来越多的生物数据需要通过复杂的计算工具（集群、云端和网格计算）进行NGS处理和分析。

1. Arvados http://arvados.org
产品级的数据科学平台，能处理大数据集，由两个主要系统组成以及涵盖很多相关服务与组件，包括API SDK和虚拟化工具。

2. Taverna http://www.taverna.org.uk/
一个与具体领域无关的独立的工作流管理系统，包括一系列工具用于设计和科学工作流程的实现。

3. Galaxy http://galaxyproject.org/
基于web用于数据密集的生物医学研究

4. SHIWA http://www.erflow.eu/
跨国的欧洲工作流用户社区推出的用于科学研究的工作流。

5. Oozie https://oozie.apache.org/
是一个用于管理Apache Hadoop job的工作流调度系统。

6. DNANexus https://wiki.dnanexus.com/API-Specification-v1.0.0/IO-and-Run
不仅能在云端存储和分析文件，也有助于协助 注释和虚拟化你的数据。

7. BioDT http://www.biodatomics.com/
下一代生物信息学工具

8. Agave http://agaveapi.co/live-docs/
一个Science-as-a-Service API平台

9. DiscoveryEnvironment http://www.iplantcollaborative.org/ci/discovery-environment
iPlant 的信息基础平台

10. Wings http://www.wings-workflows.org/
是一个语义工作流系统，辅助科学家进行计算体验设计。

11. Knime https://www.knime.org/
强大的大数据分析和挖掘能力。

12. Drake https://github.com/Factual/drake
易于使用可扩展 基于文本的数据工作流工具，组织围绕数据的命令行执行，类似GNU的 Make

13. Snakemake https://bitbucket.org/johanneskoester/snakemake
是一个工作流管理系统，降低创建工作流的难度复杂性，提供快速舒服的执行环境。

14. BPipe http://bpipe.org
用于生物学领域的任务运行，用以替代各种脚本任务。

15. Ruffus https://code.google.com/p/ruffus/
Python可计算的Pipeline，用于生物信息学在并行流程中管理依赖。

16. NextFlow http://nextflow.io
借鉴Unix管道模型，提供一个流畅的DSL，允许你处理复杂的流交互。

17. Luigi http://github.com/spotify/luigi
Luigi是一个Python (2.7, 3.3, 3.4, 3.5)库包，帮助你建立复杂的批工作的管道模型pipeline，它处理依赖问题，工作流管理，虚拟化，处理失败，集成命令行等很多功能。

18. SciLuigi. 
http://github.com/samuell/sciluigi

19. GATK Queue 
https://www.broadinstitute.org/gatk/guide/topic?name=queue
建立一个分析管道模型有效率运行GATK和其他工具

20. Yabi 
https://ccg.murdoch.edu.au/yabi

21. seqware 
https://seqware.github.io/ https://seqware.github.io/docs/6-pipeline/
seqware工作流是使用java编写，在Oozie工作流引擎中执行，运行在Hadoop或SGE集群，使用Zip64文件分组工作流定义文件 包括取样设置和包含数据依赖性的单个文件。是下代基于网格和云端的数据序列分析。

22. Ketrew 
https://github.com/hammerlab/ketrew
一个提供EDSL API的OCaml库

23. Pegasus http://pegasus.isi.edu/
工作流管理系统，自动恢复和调式科学计算。

24. Airflow 
https://github.com/airbnb/airflow（重复）

25. Cosmos/ Cosmos2: 
https://github.com/LPM-HMS/COSMOS2
http://cosmos.hms.harvard.edu/COSMOS2/
主流的并行工作流Python库包，生物科学领域下一代序列流管道模型，提供命令行工具自动利用计算集群能力，提供Web仪表板监视，调试，分析你的job。

26. Pinball 
https://github.com/pinterest/pinball
Pinball是个可伸缩扩展的工作流管理器，基于组件，状态以可读格式保存，可靠，管理友好。

27. bcbio 
https://bcbio-nextgen.readthedocs.org/en/latest/
提供高吞吐量数据序列流分析，只要编写高层配置指定输入和分析参数，输入会驱动并行管道模型处理被分发的执行任务，幂等处理可重新启动，透明的事务步骤。

28. Chronos https://github.com/mesos/chronos
Chronos是一个linux cron的替代，它是分布式的失败容错的调度器，运行在 Apache Mesos之上，支持定制优化Mesos执行器作为默认的命令执行器。

29. Azkaban https://azkaban.github.io/
是一个批工作流任务调度器，由LinkedIn创建，用于运行Hadoop job，解决了job的依赖顺序，提供易于使用的Web用户界面维护和跟踪你的处理流程。

30. Apache NiFi 
https://nifi.apache.org/docs/nifi-docs/html/overview.html
系统之间数据流程的自动化，当数据流使用在各种场合，使用它自动化和管理系统之间信息流动。

31. flowr (R-based)
 http://docs.flowr.space/ https://github.com/sahilseth/flowr
Flowr让你设计和实现复杂的管道模型，部署在你的计算集群，满足生物信息学需要。

32. Mistral https://github.com/arteria-project
从主流并行序列流中处理序列数据，提供组件实现自动分析和数据管理任务作为下一代序列流中心，平衡微服务架构，使用StackStorm创建一个事件驱动的自动化系统。灵活可伸缩。

33. nipype http://nipy.org/nipype/

34. End of Day https://github.com/joestubbs/endofday
docker 容器的可执行工作流，可以使用yaml文件定义。

35. BioDSL https://github.com/maasha/BioDSL
用于生物学的领域特定语言。

36. BigDataScript http://pcingola.github.io/BigDataScript/
在笔记本上开发的数据分析管道模型可以运行在大数据几千节点集群上。

37. Omics Pipe: 
 http://sulab.scripps.edu/omicspipe/
开源模块计算平台，自动化multi-omics数据分析管道模型的最佳实践。

38. Ensembl Hive 
https://github.com/Ensembl/ensembl-hive
eHive是一个在分布式计算资源运行计算管道模型的系统。

39. QuickNGS 
http://bifacility.uni-koeln.de/quickngs/web
下一代测序数据的高吞吐量的数据分析。

40. GenePattern 
http://www.broadinstitute.org/cancer/software/genepattern/
提供数百个分析工具，分析 gene expression (RNA-seq 和 microarray), sequence variation and copy number, proteomic, flow cytometry, 和网络分析

41. Chipster http://chipster.csc.fi/
新一代测序(NGS)，提供超过350分析工具

42. The Genome Modeling System https://github.com/genome/gms

43. Cuneiform,  https://github.com/joergen7/cuneiform
函数式工作流语言

45. Anvaya http://www.ncbi.nlm.nih.gov/pubmed/22809419
自动化基因分析的工作流环境

46. Makeflow http://ccl.cse.nd.edu/software/makeflow/
在集群 云端和网格之上执行大型复杂工作流引擎

47. Airavata http://airavata.apache.org/
基于集群，云端和网格之上组合，管理，执行和监视大规模可伸缩应用和工作流引擎

48. Pyflow https://github.com/Illumina/pyflow
一个轻量的并行任务引擎

49. Clusterflow https://github.com/ewels/clusterflow
一个管道模型工具，在集群环境自动化和标准化生物分析。

50. Unipro UGENE http://ugene.net/ https://dx.doi.org/10.7717/peerj.644
运行在windows Mac和Linux。

51. CloudSlang http://www.cloudslang.io/
管理协调Docker和CoreOS应用，快速化自动DevOps 

52. Stacks http://catchenlab.life.illinois.edu/stacks/
用于构建Ioci的软件管道模型

53. Leaf http://www.francesconapolitano.it/leaf/index.html
用于数据流Bioinformatic Protocol的设计和管理的Python工具

54. omictools http://omictools.com/
提供11573 种分析工具

55. Job 描述语言
.https://edms.cern.ch/ui/file/590869/1/WMS-JDL.pdf

56. YAWL 
http://www.yawlfoundation.org/
一个BPM/工作流系统，基于简明和强大的模型语言，处理复杂数据转换，完全集成各种Web服务。

57. Triquetrum
https://github.com/eclipse/triquetrum/
科学工作流的管理和执行。

58. Kronos https://github.com/jtaghiyar/kronos
癌症和肿瘤信息分析

59. qsubsec 
https://github.com/alastair-droop/qsubsec
基于SGE grid system的模板语言，产生用于提交任务的脚本语言。

60. YesWorkflow http://yesworkflow.org
将工作流模型带到脚本语言中

61. GWF - Grid WorkFlow 
https://github.com/mailund/gwf http://mailund.github.io/gwf/
小的类似make的通过qsub提交工作流的工具。

62. Fireworks. https://pythonhosted.org/FireWorks/
是一个定义 管理和执行工作流的框架，能使用 Python, JSON, 或 YAML定义复杂工作流，存储在MongoDB中，能够通过Web界面监视，工作流执行能自动跨无数个计算资源执行。

63. NGLess https://github.com/luispedro/ngless
是下一代测序NGS 的领域特定语言。
