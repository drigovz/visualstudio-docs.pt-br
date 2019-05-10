---
title: Novidades no design no Visual Studio 2017
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
ms.openlocfilehash: dc75c7414e0fff18f76d14f8f9a4e0779a9e7a2b
ms.sourcegitcommit: 6a19c5ece38a70731496a38f2ef20676ff18f8a4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/09/2019
ms.locfileid: "65476545"
---
# <a name="whats-new-for-design-in-visual-studio-2017"></a>Novidades no design no Visual Studio 2017

## <a name="live-dependency-validation"></a>Validação de dependência dinâmica

Remover dependências indesejáveis é uma parte importante de gerenciar a dívida técnica. O Visual Studio fornece validação em tempo real das dependências, incluindo informações precisas sobre problemas, como onde eles estão localizados. Dependências em tempo real validação usa todas as vantagens dos novos recursos na lista de erros e o editor.

![Validação de dependência dinâmica em ação](media/dep-validation-whatsnew-01.png)

A experiência de criação foi alterado para fazer a validação de dependência mais detectáveis e mais acessível. A terminologia foi alterado de "Diagrama de camada" para "Diagrama de dependência".

O **arquitetura** menu agora contém um comando para criar diretamente um diagrama de dependência:

![Item de dependências em tempo real no menu de arquitetura](media/dep-validation-whatsnew-02.png)

Nomes de propriedade de camada e as descrições foram alteradas para torná-los mais significativos:

![Nomes de propriedade de dependência ao vivo atualizado](media/dep-validation-whatsnew-03.png)

Verá imediatamente o impacto das alterações nos resultados da análise para o código na solução atual de cada vez que você salva o diagrama. Você não precisa aguardar a conclusão do **validar dependências** comando.

Para obter mais detalhes, consulte [esta postagem de blog](https://devblogs.microsoft.com/devops/live-architecture-dependency-validation-in-visual-studio-15-preview-5/).

## <a name="uml-designers-have-been-removed"></a>Designers UML foram removidos

Os designers UML foram removidos do Visual Studio.

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

Suporte para visualizar a arquitetura do .NET e C++ código está disponível por meio [mapas de código](map-dependencies-across-your-solutions.md).

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