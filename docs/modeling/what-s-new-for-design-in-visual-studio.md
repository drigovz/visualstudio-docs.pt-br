---
title: O que há de novo no design no Visual Studio 2017
titleSuffix: ''
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- what's new [Visual Studio], architecture and modeling
- architecture [Visual Studio], modeling
- modeling software [Visual Studio], What's New
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
monikerRange: vs-2017
ms.openlocfilehash: fb7ef710d117318d475e32f19b5ca2511b94f8bc
ms.sourcegitcommit: f7c401a376ce410336846835332a693e6159c551
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57869883"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>O que há de novo no design no Visual Studio 2017

## <a name="live-dependency-validation"></a>Validação de dependência dinâmica

Remover dependências indesejáveis é uma parte importante de gerenciar a dívida técnica. Validação em tempo real de dependências é agora incluído, fornecendo informações precisas sobre problemas e se beneficia totalmente os novos recursos na lista de erros e o editor.

![Validação de dependência dinâmica em ação](media/dep-validation-whatsnew-01.png)

A experiência de criação foi alterado para fazer a validação de dependência mais detectáveis e mais acessível, alterando a terminologia de "Diagrama de camada" para "Diagrama de dependência".

O **arquitetura** menu agora contém um comando para criar diretamente um diagrama de dependência:

![Item de dependências em tempo real no menu de arquitetura](media/dep-validation-whatsnew-02.png)

... e os nomes de propriedade de uma camada em um diagrama de dependência e suas descrições, foram alterados para torná-los mais significativos:

![Nomes de propriedade de dependência ao vivo atualizado](media/dep-validation-whatsnew-03.png)

Agora você ver o impacto das alterações imediatamente nos resultados da análise para o código na solução atual de cada vez que você salva o diagrama. Você não precisa mais esperar pela conclusão do comando "Validar dependências".

Para obter mais detalhes, consulte [esta postagem de blog](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Designers UML foram removidos

Os designers UML foram retirados desta versão do Visual Studio Enterprise.

* Diagramas de UML agora são apresentados como arquivos XML
* O Gerenciador de modelos UML não existe mais
* Referências não são mais usadas para validação de dependência de projeto de modelagem
* O nó de "Referências de camada" no Gerenciador de soluções não é mais exibido
* A ação de build "Validar" em um diagrama de dependência (camada) não é mais usada – a tarefa de Build foi removida
* A estrutura do projeto é mantida para o ciclo completo entre versões
* Você ainda pode abrir, criar, editar e salvar um diagrama de dependência (camada) como XML
* Itens de trabalho do TFS vinculados a um diagrama de dependência (camada) não são acessíveis na superfície de design
* Não há suporte para o back-vinculação de DSL ou uma camada
* Não há suporte para extensibilidade o SDK de modelagem UML

Entretanto, há suporte para visualizar a arquitetura de código .NET e C++ está disponível por meio [mapas de código](map-dependencies-across-your-solutions.md)e os aperfeiçoamentos significativos para validação de dependência descrito acima.

Se você for um usuário significativas dos designers UML, você pode continuar a usar o Visual Studio 2015 ou versões anteriores enquanto você decidir sobre uma ferramenta alternativa para suas necessidades UML.

Para obter mais detalhes, consulte [esta postagem de blog](https://devblogs.microsoft.com/devops/uml-designers-have-been-removed-layer-designer-now-supports-live-architectural-analysis/).

[!INCLUDE[modeling_sdk_info](includes/modeling_sdk_info.md)]

## <a name="a-nameversionsupport-edition-support-for-architecture-and-modeling-tools"></a><a name="VersionSupport" />Suporte de edição para a arquitetura e ferramentas de modelagem

Visual Studio está disponível em várias edições. Nem todos eles oferecem suporte para a arquitetura e ferramentas de modelagem. A tabela a seguir mostra a disponibilidade de cada ferramenta.

|**Recurso**|**Edição Enterprise**|**Professional edition**|**Edição de comunidade**|
|-|-|-|-|
|**Mapas de código**|Sim|Só oferece suporte à leitura de mapas de código, código de filtragem mapas, adicionar novos nós genéricos e criando um novo gráfico direcionado a partir de uma seleção.|-|
|**Diagramas de dependência**|Sim|Só dá suporte à leitura de diagramas de dependência.|Só dá suporte à leitura de diagramas de dependência.|
|**Gráficos direcionados** (diagramas DGML)|Sim|Sim|Sim|
|**Clone de código**|Sim|-|-|