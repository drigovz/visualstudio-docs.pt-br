---
title: Estender modelos e diagramas uml | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending
- UML model, extending
ms.assetid: b5bfa61e-ea59-4c3b-b5af-53475d7d13cd
caps.latest.revision: 39
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 7f4c490abbcd5b970c5bf9586ea881be4c5d62a4
ms.sourcegitcommit: 95f26af1da51d4c83ae78adcb7372b32364d8a2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/13/2020
ms.locfileid: "79302325"
---
# <a name="extend-uml-models-and-diagrams"></a>Estender modelos e diagramas UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tópico resume as diferentes maneiras pelas quais você pode estender as ferramentas de modelagem UML incluídas no Visual Studio. Para ver quais versões do Visual Studio suportam cada tipo e ferramenta de modelo, consulte [suporte à versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 No cenário de exemplo a seguir, a Fabrikam projeta e instala sistemas de manuseio de bagagem de aeroportos. De um projeto de aeroporto para o outro, há muitas semelhanças nos equipamentos básicos e no software que o controla. No entanto, há também vários fatores que variam amplamente, como a configuração de correias transportadoras, mesas de checkin, caixas de armazenamento e outros equipamentos de manuseio de bolsas.

 Ao iniciar um novo projeto, a equipe da Fabrikam cria um modelo UML para ajudá-los a discutir esses requisitos entre si e com seu cliente. Eles usam diagramas de atividade para representar o fluxo de sacos, com nós de objeto representando cada peça de equipamento. O modelo UML não representa diretamente o código do sistema.

 A equipe de ferramentas da Fabrikam faz uma série de melhorias para ajudar as equipes de desenvolvimento. As seções a seguir descrevem os diferentes tipos de extensões que você pode definir. Você pode combinar várias dessas técnicas em uma extensão do Visual Studio.

 Para obter mais informações, consulte este vídeo: ![link para vídeo](../data-tools/media/playvideo.gif "PlayVideo")[MSDN How Do I Series: UML Tools and Extensibility](https://msdn.microsoft.com/vstudio/ff859492).

## <a name="requirements"></a><a name="Requirements"></a>Requisitos

- [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

- [Modelagem SDK para Visual Studio 2015](https://www.microsoft.com/download/details.aspx?id=48148).

## <a name="profiles"></a>Perfis
 Os perfis permitem definir estereótipos e propriedades adicionais em elementos UML.

 Os desenvolvedores de ferramentas da Fabrikam definem estereótipos nos nós de objetos de diagramas de atividade, como "correia transportadora" e "mesa de checkin". Quando um membro da equipe cria um esquema de manuseio de bagagem usando um diagrama de atividade, agora ele pode definir estereótipos para indicar que tipo de equipamento cada nó representa. Os desenvolvedores da ferramenta definem propriedades adicionais em alguns dos estereótipos, para que os usuários possam registrar valores como a capacidade de uma correia transportadora e a entrega de uma mesa de check-in.

 Para obter mais informações, consulte [Definir um perfil para estender umL](../modeling/define-a-profile-to-extend-uml.md).

## <a name="custom-toolbox-items"></a>Itens personalizados da caixa de ferramentas
 Um item de caixa de ferramentas personalizado cria um elemento ou um grupo de elementos de um protótipo que você define em um diagrama. Por exemplo, você pode criar uma ferramenta que cria casos de uso em uma determinada cor ou estereótipo, ou um grupo de classes e associações que representa um padrão de design. Você pode adicionar esses itens da caixa de ferramentas às extensões do Visual Studio e distribuí-los para outros usuários.

 Para obter mais informações, consulte [Definir um item de caixa de ferramentas de modelagem personalizada](../modeling/define-a-custom-modeling-toolbox-item.md).

## <a name="validation"></a>Validação
 Você pode definir regras para garantir que um modelo UML esteja em conformidade com as restrições especificadas.

 Os desenvolvedores de ferramentas da Fabrikam definem regras para ajudar os membros da equipe a evitar erros simples nos modelos de manuseio de bagagem. Por exemplo, uma mesa de check-in não pode ser conectada diretamente a uma caixa de armazenamento. Deve haver pelo menos uma correia transportadora entre eles.

 Para obter mais informações, consulte [Definir restrições de validação para modelos UML](../modeling/define-validation-constraints-for-uml-models.md).

## <a name="menu-commands"></a>Comandos de menu
 Você pode definir comandos que os usuários podem invocar clicando com o botão direito do mouse em um diagrama UML. Os comandos podem atualizar o modelo e [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]diagramas ou executar outras operações em .

 Fabrikam define comandos de menu para automatizar operações realizadas com freqüência, como criar uma mesa de check-in e conectá-la a uma correia transportadora selecionada ou reorganizar um diagrama de acordo com as regras de layout da empresa.

 Consulte [Definir um comando de menu em um diagrama de modelagem](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

## <a name="gestures"></a>Gestos
 Você pode definir comandos que os usuários iniciam clicando duas vezes em um elemento de diagrama, ou arrastando para um diagrama ou um elemento no diagrama. Você pode definir comandos que podem lidar com itens arrastados de outros diagramas uml, de outras partes do Visual Studio, ou de outros aplicativos ou Windows Explorer (ou Explorador de Arquivos).

 Os membros da equipe fabrikam podem associar um arquivo como uma especificação com qualquer elemento do modelo arrastando-o da área de trabalho do Windows. Os desenvolvedores de ferramentas definiram um estereótipo que fornece qualquer elemento com uma propriedade de caminho de arquivo e um gesto que define o estereótipo e o caminho do arquivo quando um arquivo é lançado em um elemento.

 Para obter mais informações, consulte [Definir um manipulador de gestos em um diagrama de modelagem](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).

## <a name="responding-to-changes"></a>Respondendo às alterações
 Você pode escrever código que responda a alterações no modelo, seja causadas por ações do usuário ou por outro código do programa.

 Os desenvolvedores da Fabrikam criam código que define automaticamente a cor de um elemento dependente de seu estereótipo. Isso facilita para os usuários distinguir as diferentes funções desempenhadas pelos elementos nos modelos.

 Para obter mais informações, consulte [Como responder a alterações em um modelo UML](../misc/how-to-respond-to-changes-in-a-uml-model.md).

## <a name="model-bus"></a>Ônibus modelo
 O Model Bus permite que você acesse um [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)] diagrama ou modelo de outro diagrama ou de outra extensão. Entre outras coisas, isso permite que você espalhe informações em mais de um modelo, para que várias pessoas possam trabalhar no modelo combinado ao mesmo tempo.

 Fabrikam usa elementos em diagramas de atividade para representar equipamentos de manuseio de bagagem. Cada item do equipamento pode ter uma especificação mais detalhada em outro diagrama, que pode estar em outro modelo. As restrições de validação no diagrama de fluxo de bagagem podem recuperar propriedades relevantes do equipamento a partir dos outros diagramas. As referências aos outros diagramas são armazenadas em propriedades adicionais definidas em estereótipos.

 Para obter mais informações, consulte [Integrar modelos UML com outros modelos e ferramentas](../modeling/integrate-uml-models-with-other-models-and-tools.md).

## <a name="generation"></a>Generation
 A partir de um modelo, você pode gerar código de programa, scripts, configurações, documentos, novos modelos ou outros artefatos.

 Nos sistemas de bagagem que Fabrikam projeta, grande parte do código do programa é o mesmo de um projeto para o outro. O principal aspecto variável é o plano do fluxo de bagagem ao redor do aeroporto. Depois que a equipe de design teve a experiência de seus primeiros projetos, os desenvolvedores de ferramentas criam um modelo que gera, a partir do modelo de fluxo de bagagem, grande parte do código do programa variável e outros arquivos, como documentos do usuário. Isso reduz consideravelmente o tempo de desenvolvimento e a taxa de erro para cada novo projeto.

 Para obter mais informações, consulte [Gerar arquivos a partir de um modelo UML](../modeling/generate-files-from-a-uml-model.md).

## <a name="team-foundation-server-integration"></a>Integração do Servidor da Fundação team
 Você pode vincular itens de trabalho a elementos de modelo e acessar os itens vinculados de forma programática.

 Os desenvolvedores de ferramentas da Fabrikam escrevem uma ferramenta que gera um cronograma de trabalho para cada projeto do aeroporto. Os itens de trabalho no cronograma estão ligados aos elementos do modelo.

 Para obter mais informações, consulte [Definir um manipulador de link de item de trabalho](../modeling/define-a-work-item-link-handler.md).

## <a name="tools-that-update-models"></a>Ferramentas que atualizam modelos
 Você pode criar aplicativos autônomos e extensões do Visual Studio que podem carregar modelos UML.

 Os desenvolvedores da Fabrikam criam uma ferramenta que lê um modelo e gera relatórios do progresso do trabalho em cada elemento do modelo.

 Para obter mais informações, consulte [Leia um modelo UML no código do programa](../modeling/read-a-uml-model-in-program-code.md).

## <a name="domain-specific-languages"></a>Idiomas específicos de domínio
 Quando você usa frequentemente um determinado tipo de modelo, ele pode ser útil para criar uma linguagem específica de domínio. Isso pode ser feito para atender às necessidades do seu negócio mais de perto do que um modelo UML, mas requer mais esforço para construí-lo e mantê-lo. Para obter mais informações, consulte [Modeling SDK for Visual Studio - Domain-Specific Languages](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).

## <a name="external-resources"></a>Recursos externos

|**Categoria**|**Links**|
|------------------|---------------|
|**Vídeos**|![link para vídeo](../data-tools/media/playvideo.gif "PlayVideo") [MSDN Como Faço Série: Ferramentas uml e extensibilidade](https://msdn.microsoft.com/vstudio/ff859492)<br /><br /> ![link para vídeo](../data-tools/media/playvideo.gif "PlayVideo") [Canal 9: UML com Visual Studio](https://channel9.msdn.com/posts/clinted/)|
|**Fóruns**|-   [Visual Studio Visualização & Ferramentas de Modelagem](https://social.msdn.microsoft.com/Forums/en-US/home?forum=vsarch)<br />-   [Visual Studio Visualização & Modelagem SDK (Ferramentas DSL)](https://social.msdn.microsoft.com/Forums/home?forum=dslvsarchx)|
|**Blogues**|[Visual Studio ALM + Team Foundation Server Blog](https://blogs.msdn.com/b/visualstudioalm)|
|**Artigos técnicos e revistas**|[Centro de Arquitetura MSDN](https://msdn.microsoft.com/architecture/default.aspx)|

## <a name="see-also"></a>Consulte Também
 [Crie modelos para o aplicativo](../modeling/create-models-for-your-app.md) [API Reference for UML Modeling Extensibility](../modeling/api-reference-for-uml-modeling-extensibility.md)
