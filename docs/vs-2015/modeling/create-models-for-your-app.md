---
title: Criar modelos para seu aplicativo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
f1_keywords:
- vs.teamarch.common.commentlink.properties
- vs.teamarch.UMLModelExplorer.dependency
- vs.teamarch.UMLModelExplorer.commentlink
- vs.teamarch.common.dependency.properties
- Microsoft.VisualStudio.Uml.Diagrams.CommentShape.IsTransparent
- vs.teamarch.common.comment.properties
- vs.teamarch.UMLModelExplorer.comment
helpviewer_keywords:
- diagrams - modeling, sequence
- software design
- diagrams - modeling, use case
- diagrams - modeling, component
- diagrams - modeling, UML component
- UML model
- diagrams - modeling, UML use case
- diagrams - modeling, class
- diagrams - modeling, activity
- diagrams - modeling, UML activity
- software modeling
- diagrams - modeling, UML sequence
- UML
- diagrams - modeling, UML
- diagrams - modeling, layer
- software, designing
- diagrams - modeling, UML class
- software, modeling
- UML diagrams
ms.assetid: b69d9d91-c7e7-4dee-8eb6-706076eecb85
caps.latest.revision: 60
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7e1b37a357113be010ea336fc5666beb8cd33dbc
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "75852015"
---
# <a name="create-models-for-your-app"></a>Criar modelos para o aplicativo
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os diagramas de modelagem ajudam você a entender, esclarecer e comunicar ideias sobre seu código e os requisitos de usuário para os quais seu sistema de software deve dar suporte. Por exemplo, para descrever e comunicar os requisitos do usuário, você pode usar os diagramas de caso de uso, atividade, classe e sequência do Unified Modeling Language (UML). Para descrever e comunicar a funcionalidade do seu sistema, você pode usar os diagramas de componente, classe, atividade e Sequência UML.

 Consulte [vídeo do Channel 9: melhorar a arquitetura por meio de modelagem](https://s.ch9.ms/Series/Visual-Studio-2012-Premium-and-Ultimate-Overview/Visual-Studio-Ultimate-2012-Improving-architecture-through-modeling).

 Você pode criar os seguintes diagramas UML nesta versão:

|**Diagrama**|**programas**|
|-----------------|---------------|
|[Diagramas de atividade UML: referência](../modeling/uml-activity-diagrams-reference.md)|Fluxo de trabalho entre ações e participantes em um processo de negócios|
|[Diagramas de componente UML: referência](../modeling/uml-component-diagrams-reference.md)|Componentes de um sistema, suas interfaces, portas e relações|
|[Diagramas de classe UML: referência](../modeling/uml-class-diagrams-reference.md)|Tipos que são usados para armazenar e trocar dados no sistema e suas relações|
|[Diagramas de sequência UML: referência](../modeling/uml-sequence-diagrams-reference.md)|Sequências de interações entre objetos, componentes, sistemas ou atores|
|[Diagramas de caso de uso UML: referência](../modeling/uml-use-case-diagrams-reference.md)|Metas de usuário e tarefas às quais um sistema dá suporte|

 Para ver quais versões do Visual Studio oferecem suporte a cada tipo de diagrama, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Para visualizar a arquitetura de um sistema ou de um código existente, crie os seguintes diagramas:

|**Diagrama**|**programas**|
|-----------------|---------------|
|[Diagramas de camada: diretrizes](../modeling/layer-diagrams-guidelines.md)<br /><br /> [Diagramas de camada: referência](../modeling/layer-diagrams-reference.md)|Arquitetura de alto nível do sistema|
|Mapas de código<br /><br /> [Mapear as dependências nas soluções](../modeling/map-dependencies-across-your-solutions.md)<br /><br /> [Encontrar possíveis problemas usando analisadores de mapa de códigos](../modeling/find-potential-problems-using-code-map-analyzers.md)|Dependências e outras relações no código existente|
|Diagramas de classe gerados por código<br /><br /> [Trabalhando com diagramas de classe (Designer de Classe)](../ide/working-with-class-diagrams-class-designer.md)|Tipos e suas relações no código .NET|

## <a name="common-tasks"></a>Tarefas comuns

|**Tópico**|**Tarefa**|
|---------------|--------------|
|[Criar projetos e diagramas de modelagem UML](../modeling/create-uml-modeling-projects-and-diagrams.md)|**Crie modelos** e adicione diagramas.|
|[Editar modelos e diagramas UML](../modeling/edit-uml-models-and-diagrams.md)|**Desenhe diagramas** para editar o modelo.|
|[Definir pacotes e namespaces](../modeling/define-packages-and-namespaces.md)|**Crie pacotes** para dividir um modelo em unidades em que diferentes membros da equipe podem trabalhar.|
|[Gerar código por meio de diagramas de classe UML](../modeling/generate-code-from-uml-class-diagrams.md)|**Gere código C# de diagramas de classe** para iniciar sua implementação.|
|[Personalizar o modelo com perfis e estereótipos](../modeling/customize-your-model-with-profiles-and-stereotypes.md)|**Personalize elementos de modelo** usando estereótipos para estender os elementos de modelo UML padrão para fins específicos.|
|[Vincular elementos de modelo e itens de trabalho](../modeling/link-model-elements-and-work-items.md)|**Crie links entre elementos de modelo e itens de trabalho** para ajudá-lo a acompanhar tarefas, casos de teste, bugs, requisitos, problemas ou outros tipos de trabalho associados a partes específicas do seu modelo.|
|[Exportar diagramas como imagens](../modeling/export-diagrams-as-images.md)|**Salve seu modelo e diagramas** para que você possa compartilhá-los com outros usuários, incluindo aqueles que não usam [!INCLUDE[vsUltShort](../includes/vsultshort-md.md)] .|

## <a name="related-tasks"></a>Related Tasks

|**Tópico**|**Tarefa**|
|---------------|--------------|
|[Visualizar código](../modeling/visualize-code.md)|Crie mapas de código e diagramas de camada para entender melhor o código desconhecido.|
|[Requisitos de usuário do modelo](../modeling/model-user-requirements.md)|Use modelos para esclarecer e comunicar as necessidades dos usuários.|
|[Modelar a arquitetura do aplicativo](../modeling/model-your-app-s-architecture.md)|Use modelos para descrever a estrutura geral e o comportamento do seu sistema e garantir que ele atenda às necessidades dos usuários.|
|[Validar o sistema durante o desenvolvimento](../modeling/validate-your-system-during-development.md)|Certifique-se de que seu software permaneça consistente com as necessidades de seus usuários e a arquitetura geral do seu sistema.|
|[Usar modelos no processo de desenvolvimento](../modeling/use-models-in-your-development-process.md)<br /><br /> [Usar modelos no desenvolvimento ágil](https://msdn.microsoft.com/592ac27c-3d3e-454a-9c38-b76658ed137f)|Use modelos para ajudá-lo a entender e alterar seu sistema durante seu desenvolvimento.|
|[Estruturar a solução de modelagem](../modeling/structure-your-modeling-solution.md)|Organize modelos em um projeto grande ou médio.|

## <a name="external-resources"></a>Recursos externos

|**Categoria**|**Links**|
|------------------|---------------|
|**Fóruns**|-   [Ferramentas de modelagem & de visualização do Visual Studio](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [SDK de modelagem de & de visualização do Visual Studio (ferramentas DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
