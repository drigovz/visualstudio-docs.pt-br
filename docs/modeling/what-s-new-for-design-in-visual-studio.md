---
title: Novidades no design no Visual Studio 2017
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: JoshuaPartlow
ms.author: joshuapa
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: 6f81cc32604abe6d90ac0d263574e97df35c63bd
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302948"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Novidades no design no Visual Studio 2017

## <a name="live-dependency-validation"></a>Validação de dependência ao vivo

Remover dependências indesejadas é uma parte importante da gestão de sua dívida técnica. O Visual Studio fornece validação ao vivo de dependências, incluindo informações precisas sobre problemas, como onde eles estão localizados. A validação de dependência ao vivo tira todas as vantagens dos novos recursos na Lista de Erros e no editor.

![Validação de dependência ao vivo em ação](media/dep-validation-whatsnew-01.png)

A experiência de autoria mudou para tornar a validação da dependência mais descoberta e acessível. A terminologia mudou de "Diagrama de camada" para "Diagrama de dependência".

O menu **Arquitetura** agora contém um comando para criar diretamente um diagrama de dependência:

![Item de dependência ao vivo no menu Arquitetura](media/dep-validation-whatsnew-02.png)

Os nomes e descrições das propriedades de camada foram alterados para torná-los mais significativos:

![Dependência ao vivo atualizou nomes de propriedades](media/dep-validation-whatsnew-03.png)

Você vê imediatamente o impacto de suas alterações nos resultados de análise para o código atual na solução cada vez que você salvar o diagrama. Você não precisa esperar pela conclusão do comando **Valid dependências.**

Para obter mais detalhes, consulte [esta postagem no blog](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Os designers da UML foram removidos

Os designers da UML foram removidos do Visual Studio.

* Diagramas UML são agora apresentados como arquivos XML
* O UML Model Explorer não existe mais
* As referências do projeto de modelagem não são mais usadas para validação de dependência
* O nó "Referências em camadas" no Solution Explorer não é mais exibido
* A ação de compilação "Validar" em um diagrama de dependência (Camada) não é mais usada - a tarefa Construir foi removida
* A estrutura do projeto é mantida para tropeços redondos entre versões
* Você ainda pode abrir, criar, editar e salvar um diagrama de Dependência (Camada) como XML
* Os itens de trabalho do TFS vinculados a um diagrama de Dependência (Camada) não estão acessíveis na superfície do projeto
* A vinculação de volta a DSL ou uma camada não é mais suportada
* A extensibilidade uml no Modeling SDK não é mais suportada

O suporte para visualizar a arquitetura do código .NET e C++ está disponível através de [mapas de código](map-dependencies-across-your-solutions.md).

Se você é um usuário significativo dos designers uml, você pode continuar a usar o Visual Studio 2015 ou versões anteriores enquanto você decide sobre uma ferramenta alternativa para suas necessidades UML.

Para obter mais detalhes, consulte [esta postagem no blog](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Suporte de edição para ferramentas de arquitetura e modelagem

Visual Studio está disponível em várias edições. Nem todas elas fornecem suporte para as ferramentas de arquitetura e modelagem. A tabela a seguir mostra a disponibilidade de cada ferramenta.

|**Recurso**|**Edição corporativa**|**Edição profissional**|**Edição comunitária**|
|-|-|-|-|
|**Mapas de código**|Sim|Apenas suporta a leitura de mapas de código, filtração de mapas de código, adição de novos nódulos genéricos e a criação de um novo Gráfico Direcionado a partir de uma seleção.|-|
|**Diagramas de dependência**|Sim|Só suporta diagramas de dependência de leitura.|Só suporta diagramas de dependência de leitura.|
|**Gráficos direcionados** (diagramas DGML)|Sim|Sim|Sim|
|**Clone de código**|Sim|-|-|
