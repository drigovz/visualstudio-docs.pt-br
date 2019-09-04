---
title: Carga de trabalho para Aplicativos de ciência de dados e análise
description: Esta carga de trabalho do Visual Studio reúne o Python, o F# e suas respectivas distribuições de tempo de execução, incluindo o Anaconda. (O R também está incluído somente no Visual Studio 2017.)
ms.date: 02/28/2019
ms.topic: overview
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- python
- data-science
ms.openlocfilehash: 44906d70be05891fe52096adec2f61f2261b5db5
ms.sourcegitcommit: 3cda0d58c5cf1985122b8977b33a171c7359f324
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/29/2019
ms.locfileid: "70154886"
---
# <a name="install-data-science-support-in-visual-studio"></a>Instalar o suporte para ciência de dados no Visual Studio

A carga de trabalho de Aplicativos de Ciência de Dados e Analíticos, selecionada e instalada por meio do Instalador do Visual Studio, reúne várias linguagens e suas respectivas distribuições de tempo de execução:

::: moniker range="vs-2017"
- [Python e Anaconda](../python/overview-of-python-tools-for-visual-studio.md)
- [F# com o .NET Framework](/dotnet/fsharp/)
- [R e Microsoft R Client](../rtvs/index.md)
::: moniker-end

::: moniker range="vs-2019"
- [Python](../python/overview-of-python-tools-for-visual-studio.md)
- [F# com o .NET Framework](/dotnet/fsharp/)
::: moniker-end

![Carga de trabalho para Aplicativos de ciência de dados e análise no Instalador do Visual Studio](media/workload/data-science-workload.png)

::: moniker range="vs-2017"
O Python e o R são duas das linguagens de script principais usadas para ciência de dados. Essas duas linguagens são fáceis de aprender e compatíveis com um rico ecossistema de pacotes. Esses pacotes abordam uma ampla variedade de cenários, como aquisição de dados, limpeza, treinamento de modelo, implantação e criação de gráficos. O F# também é uma linguagem avançada do .NET que prima pela funcionalidade e é adequada a uma ampla variedade de tarefas de processamento de dados.
::: moniker-end

::: moniker range="vs-2019"
O Python é uma das linguagens de script principais usadas para ciência de dados. O Python é fácil de aprender e é compatível com um rico ecossistema de pacotes. Esses pacotes abordam uma ampla variedade de cenários, como aquisição de dados, limpeza, treinamento de modelo, implantação e criação de gráficos. O F# também é uma linguagem avançada do .NET que prima pela funcionalidade e é adequada a uma ampla variedade de tarefas de processamento de dados. (Para a linguagem R, recomendamos o [Azure Notebooks](https://notebooks.azure.com).)
::: moniker-end

<!--Note link on the image because this one is large -->
[![Capturas de tela do Visual Studio com R, Python e F#](media/workload/data-science-workload-screens.png)](media/workload/data-science-workload-screens.png#lightbox)

## <a name="workload-options"></a>Opções de carga de trabalho

Por padrão, a carga de trabalho instala as opções a seguir, que você pode modificar na seção de resumo da carga de trabalho no Instalador do Visual Studio:

::: moniker range="vs-2019"
- Suporte à linguagem F# da área de trabalho
- Python:
  - Suporte da linguagem Python
  - Suporte Web do Python
::: moniker-end

::: moniker range="vs-2017"
- Suporte à linguagem F#
- Python:
  - Suporte da linguagem Python
  - [Anaconda3 de 64 bits](https://www.continuum.io), uma distribuição Python que inclui bibliotecas de ciência de dados abrangentes e um interpretador Python.
  - Suporte Web do Python
  - Suporte do modelo Cookiecutter
- R:
  - Suporte à linguagem R
  - Suporte de tempo de execução para ferramentas de desenvolvimento do R
  - [Microsoft R Client](/machine-learning-server/r-client/what-is-microsoft-r-client) (O interpretador R totalmente compatível e com suporte da comunidade da Microsoft com bibliotecas ScaleR para computação mais rápida em nós únicos ou clusters. Você também pode usar qualquer R do [CRAN](https://cran.r-project.org/).)
::: moniker-end

## <a name="sql-server-integration"></a>Integração ao SQL Server

::: moniker range="vs-2017"
O SQL Server dá suporte ao uso do Python e do R para análises avançadas diretamente no SQL Server. O suporte ao R é incluído com o SQL Server 2016 e posterior; o suporte ao Python está disponível no SQL Server 2017 CTP 2.0 e posterior.
::: moniker-end

::: moniker range=">=vs-2019"
O SQL Server dá suporte ao uso do Python para análises avançadas diretamente no SQL Server. O suporte ao Python está disponível no SQL Server 2017 CTP 2.0 e posterior.
::: moniker-end

Aproveite as seguintes vantagens executando o código no local em que os dados já residem:

- **Eliminação da movimentação de dados**: Em vez de mover os dados do banco de dados para o aplicativo ou o modelo, você pode criar aplicativos no banco de dados. Essa funcionalidade elimina os obstáculos de segurança, de conformidade, de governança, de integridade, bem como um host de problemas semelhantes relacionados à movimentação de grandes quantidades de dados. Também consuma conjuntos de dados que não se ajustam à memória de um computador cliente.

- **Implantação fácil**: Depois que você preparar um modelo, sua implantação em produção é uma simples questão de inseri-lo em um script T-SQL. Os aplicativos cliente SQL codificados em qualquer linguagem poderão aproveitar os modelos e a inteligência por meio de uma chamada de procedimento armazenado. Nenhuma integração de linguagem específica é necessária.

- **Desempenho e escala de nível empresarial**: Use funcionalidades avançadas do SQL Server, como índices de repositório de tabelas e de colunas na memória com as APIs escalonáveis de alto desempenho nos pacotes RevoScale. A eliminação da movimentação de dados também significa que você evitará restrições de memória do cliente à medida que os dados aumentam ou que você deseja aumentar o desempenho do aplicativo.

- **Extensibilidade avançada**: Instale e execute um dos pacotes mais recentes de software livre no SQL Server para criar aplicativos de aprendizado profundo e de IA em grandes quantidades de dados no SQL Server. A instalação de um pacote no SQL Server é tão simples quanto instalar um pacote no computador local.

- **Ampla disponibilidade sem custo adicional**: As integrações de linguagem estão disponíveis em todas as edições do SQL Server 2017 e posterior, incluindo a edição Express.

Para aproveitar ao máximo a integração ao SQL Server, use o instalador do Visual Studio para instalar a carga de trabalho de **Processamento e armazenamento de dados** com a opção **SQL Server Data Tools**. A última opção habilita o SQL IntelliSense, o realce de sintaxe e a implantação.

![Carga de trabalho para Processamento e armazenamento de dados](media/workload/data-storage-workload.png) &nbsp;&nbsp;&nbsp;&nbsp; ![Opções da carga de trabalho para Processamento e armazenamento de dados](media/workload/data-storage-workload-options.png)

Para saber mais:

::: moniker range="vs-2017"
- [Trabalhar com o SQL Server e R](../rtvs/integrating-sql-server-with-r.md)
- [Análises avançadas no banco de dados com o R no SQL Server 2016 (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2016/03/29/in-database-advanced-analytics-with-r-in-sql-server-2016/)
::: moniker-end
- [Python no SQL Server 2017: aprendizado de máquina avançado no banco de dados (blog)](https://blogs.technet.microsoft.com/dataplatforminsider/2017/04/19/python-in-sql-server-2017-enhanced-in-database-machine-learning/)

## <a name="additional-services-and-sdks"></a>SDKs e serviços adicionais

Além do que está diretamente na carga de trabalho aplicativos de ciência de dados e de análise, o serviço Azure Notebooks e o SDK do Azure para Python também são úteis para ciência de dados.

O SDK do Azure para Python facilita o consumo e gerenciamento de serviços do Microsoft Azure em aplicativos executados no Windows, Mac e Linux. Para obter mais informações, veja [SDK do Azure para Python](/azure/python/).

O Azure Notebooks (atualmente em versão prévia) fornece acesso online gratuito aos blocos de anotações do Jupyter em execução na nuvem no Microsoft Azure. Como introdução, o serviço inclui blocos de anotações de exemplo em Python, em R e em F#. Visite [notebooks.azure.com](https://notebooks.azure.com/).

<!--Note link on the image because this one is large -->
[![Capturas de tela Azure Notebooks com a introdução ao exemplo em R](media/workload/data-science-workload-notebooks.png)](media/workload/data-science-workload-notebooks.png#lightbox)
