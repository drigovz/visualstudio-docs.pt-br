---
title: Estender diagramas e modelos UML | Microsoft Docs
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
ms.openlocfilehash: 69315b8a81c321d8a33583b02e9579f392d1dc65
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669603"
---
# <a name="extend-uml-models-and-diagrams"></a>Estender modelos e diagramas UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Este tópico resume as diferentes maneiras pelas quais você pode estender as ferramentas de modelagem UML incluídas com o Visual Studio. Para ver quais versões do Visual Studio dão suporte a cada tipo de modelo e ferramenta, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 No cenário de exemplo a seguir, a Fabrikam projeta e instala sistemas de manuseio de bagagem de aeroportos. De um projeto de aeroporto para o próximo, há muitas semelhanças no equipamento básico e no software que o controla. No entanto, há também vários fatores que variam muito, como a configuração de esteiras de transmissão, mesas de check-in, compartimentos de armazenamento e outros equipamentos de manuseio de saco.

 Ao iniciar um novo projeto, a equipe da Fabrikam cria um modelo UML para ajudá-los a discutir esses requisitos entre si e com seus clientes. Eles usam diagramas de atividade para representar o fluxo de bolsas, com nós de objeto representando cada parte do equipamento. O modelo UML não representa diretamente o código do sistema.

 A equipe de ferramentas da Fabrikam faz uma série de aprimoramentos para ajudar as equipes de desenvolvimento. As seções a seguir descrevem os diferentes tipos de extensões que você pode definir. Você pode combinar várias dessas técnicas em uma extensão do Visual Studio.

 Para obter mais informações, consulte este vídeo: ![link para vídeo](../data-tools/media/playvideo.gif "PlayVideo")[msdn how da Series: ferramentas e extensibilidade UML](http://go.microsoft.com/fwlink/?LinkId=214467).

## <a name="Requirements"></a> Requisitos

- [SDK do Visual Studio](../extensibility/visual-studio-sdk.md).

- [SDK de modelagem para o Visual Studio 2015](http://www.microsoft.com/download/details.aspx?id=48148).

## <a name="profiles"></a>Perfis
 Os perfis permitem que você defina estereótipos e propriedades adicionais em elementos UML.

 Os desenvolvedores de ferramentas da Fabrikam definem estereótipos nos nós de objetos de diagramas de atividade, como «esteira correia» e «checkin Desk». Quando um membro da equipe cria um esquema de manuseio de bagagem usando um diagrama de atividade, agora eles podem definir estereótipos para indicar o tipo de equipamento que cada nó representa. Os desenvolvedores de ferramentas definem propriedades adicionais em alguns dos estereótipos, para que os usuários possam registrar valores como a capacidade de uma correia de transmissão e a destro/canhoto de uma mesa de check-in.

 Para obter mais informações, consulte [definir um perfil para estender o UML](../modeling/define-a-profile-to-extend-uml.md).

## <a name="custom-toolbox-items"></a>Itens da caixa de ferramentas personalizada
 Um item de caixa de ferramentas personalizado cria um elemento ou um grupo de elementos de um protótipo que você define em um diagrama. Por exemplo, você pode criar uma ferramenta que cria casos de uso em uma cor ou estereótipo específico, ou um grupo de classes e associações que representa um padrão de design. Você pode adicionar esses itens da caixa de ferramentas a extensões do Visual Studio e distribuí-los a outros usuários.

 Para obter mais informações, consulte [definir um item da caixa de ferramentas de modelagem personalizada](../modeling/define-a-custom-modeling-toolbox-item.md).

## <a name="validation"></a>Validação
 Você pode definir regras para garantir que um modelo UML esteja de acordo com as restrições especificadas.

 Os desenvolvedores de ferramentas da Fabrikam definem regras para ajudar os membros da equipe a evitar erros simples em modelos de manipulação de bagagem. Por exemplo, uma central de check-in não pode ser conectada diretamente a uma bandeja de armazenamento. Deve haver pelo menos uma correia de transmissão entre eles.

 Para obter mais informações, consulte [definir restrições de validação para modelos UML](../modeling/define-validation-constraints-for-uml-models.md).

## <a name="menu-commands"></a>Comandos de menu
 Você pode definir comandos que os usuários podem invocar clicando com o botão direito do mouse em elementos em um diagrama UML. Os comandos podem atualizar o modelo e os diagramas ou executar outras operações no [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)].

 A Fabrikam define os comandos de menu para automatizar as operações realizadas com frequência, como criar uma central de verificação e conectá-la a uma correia de transmissão selecionada ou reorganizar um diagrama de acordo com as regras de layout da empresa.

 Consulte [definir um comando de menu em um diagrama de modelagem](../modeling/define-a-menu-command-on-a-modeling-diagram.md).

## <a name="gestures"></a>Gestos
 Você pode definir os comandos que os usuários iniciam clicando duas vezes em um elemento de diagrama ou arrastando para um diagrama ou um elemento no diagrama. Você pode definir comandos que podem lidar com itens arrastados de outros diagramas UML, de outras partes do Visual Studio ou de outros aplicativos ou do Windows Explorer (ou explorador de arquivos.

 Os membros da equipe da Fabrikam podem associar um arquivo como uma especificação com qualquer elemento de modelo arrastando-o da área de trabalho do Windows. A ferramenta que os desenvolvedores definiram um estereótipo que fornece qualquer elemento com uma propriedade de caminho de arquivo e um gesto que define o estereótipo e o caminho do arquivo quando um arquivo é Descartado em um elemento.

 Para obter mais informações, consulte [definir um manipulador de gestos em um diagrama de modelagem](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md).

## <a name="responding-to-changes"></a>Respondendo a alterações
 Você pode escrever um código que responda às alterações no modelo, seja devido a ações do usuário ou por outro código de programa.

 Os desenvolvedores da Fabrikam criam código que define automaticamente a cor de um elemento dependente de seu estereótipo. Isso facilita para os usuários a distinção das diferentes funções desempenhadas por elementos nos modelos.

 Para obter mais informações, consulte [como: responder a alterações em um modelo UML](../misc/how-to-respond-to-changes-in-a-uml-model.md).

## <a name="model-bus"></a>Barramento de modelo
 O barramento de modelo permite que você acesse um diagrama ou modelo de outro diagrama ou de outra extensão de [!INCLUDE[vs_current_short](../includes/vs-current-short-md.md)]. Entre outras coisas, isso permite que você espalhe informações em mais de um modelo, para que várias pessoas possam trabalhar no modelo combinado ao mesmo tempo.

 A Fabrikam usa elementos em diagramas de atividade para representar o equipamento de manuseio de bagagem. Cada item de equipamento pode ter uma especificação mais detalhada em outro diagrama, que pode estar em outro modelo. As restrições de validação no diagrama de fluxo bagagem podem recuperar as propriedades relevantes do equipamento dos outros diagramas. As referências aos outros diagramas são armazenadas em propriedades adicionais definidas em estereótipos.

 Para obter mais informações, consulte [integrar modelos UML com outros modelos e ferramentas](../modeling/integrate-uml-models-with-other-models-and-tools.md).

## <a name="generation"></a>Geração
 A partir de um modelo, você pode gerar código de programa, scripts, configurações, documentos, novos modelos ou outros artefatos.

 Nos sistemas bagagem que a Fabrikam projeta, grande parte do código do programa é a mesma de um projeto para o outro. O principal aspecto variável é o plano do fluxo de bagagem em todo o aeroporto. Depois que a equipe de design teve a experiência de seus primeiros projetos, os desenvolvedores de ferramentas criam um modelo que gera, do modelo de fluxo bagagem, grande parte do código de programa variável e outros arquivos, como documentos de usuário. Isso reduz consideravelmente o tempo de desenvolvimento e a taxa de erros para cada novo projeto.

 Para obter mais informações, consulte [gerar arquivos de um modelo UML](../modeling/generate-files-from-a-uml-model.md).

## <a name="team-foundation-server-integration"></a>Integração do Team Foundation Server
 Você pode vincular itens de trabalho a elementos de modelo e acessar os itens vinculados programaticamente.

 Os desenvolvedores de ferramentas da Fabrikam escrevem uma ferramenta que gera uma agenda de trabalho para cada projeto de aeroporto. Os itens de trabalho no agendamento são vinculados aos elementos do modelo.

 Para obter mais informações, consulte [definir um manipulador de link de item de trabalho](../modeling/define-a-work-item-link-handler.md).

## <a name="tools-that-update-models"></a>Ferramentas que atualizam modelos
 Você pode criar aplicativos autônomos e extensões do Visual Studio que podem carregar modelos UML.

 Os desenvolvedores da Fabrikam criam uma ferramenta que lê um modelo e gera relatórios do andamento do trabalho em cada elemento do modelo.

 Para obter mais informações, consulte [ler um modelo UML no código do programa](../modeling/read-a-uml-model-in-program-code.md).

## <a name="domain-specific-languages"></a>Linguagens específicas de domínio
 Onde você usa com frequência um tipo específico de modelo, pode ser útil criar uma linguagem específica de domínio. Isso pode ser feito para atender às suas necessidades de negócios de forma mais próxima do que um modelo UML, mas requer mais esforço para compilá-lo e mantê-lo. Para obter mais informações, consulte [SDK de modelagem para Visual Studio-linguagens específicas de domínio](../modeling/modeling-sdk-for-visual-studio-domain-specific-languages.md).

## <a name="external-resources"></a>Recursos externos

|**Categoria**|**Vincule**|
|------------------|---------------|
|**Vídeos**|![link para vídeo](../data-tools/media/playvideo.gif "PlayVideo") [série How do MSDN: ferramentas e extensibilidade UML](http://go.microsoft.com/fwlink/?LinkId=214467)<br /><br /> ![link para o canal de vídeo](../data-tools/media/playvideo.gif "PlayVideo") [9: UML com o Visual Studio](http://go.microsoft.com/fwlink/?LinkId=199957)|
|**Nos**|[ferramentas de modelagem & de visualização do Visual Studio](http://go.microsoft.com/fwlink/?LinkId=184720) -   <br />[SDK de modelagem do & de visualização do Visual Studio (ferramentas DSL)](http://go.microsoft.com/fwlink/?LinkId=184721) -   |
|**Blogs**|[Visual Studio ALM + Team Foundation Server Blog](http://go.microsoft.com/fwlink/?LinkID=201340)|
|**Artigos técnicos e diários**|[Centro de arquitetura do MSDN](http://go.microsoft.com/fwlink/?LinkId=201343)|

## <a name="see-also"></a>Consulte também
 [Criar modelos para a](../modeling/create-models-for-your-app.md) [referência de API de seu aplicativo para EXTENSIBILIDADE de modelagem UML](../modeling/api-reference-for-uml-modeling-extensibility.md)
