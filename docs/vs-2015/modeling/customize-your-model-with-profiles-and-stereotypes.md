---
title: Personalizar seu modelo com perfis e estereótipos | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, profiles
- UML model, stereotypes
- UML model, customizing
ms.assetid: fd607157-0d3a-4583-a84e-427a4b2a5acb
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b634b11418ef2d4220dc4eb07c825b514ab5494c
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74301200"
---
# <a name="customize-your-model-with-profiles-and-stereotypes"></a>Personalizar o modelo com perfis e estereótipos
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

No Visual Studio, você pode adaptar os elementos de modelo UML padrão, como classes e componentes, para personalizá-los para fins específicos. Você pode aplicar um *estereótipo* a um elemento de modelo que pode alterar a lista de propriedades do elemento. Os estereótipos são definidos em coleções chamadas *perfis*.

 Para ver quais versões do Visual Studio oferecem suporte a esse recurso, consulte [suporte de versão para ferramentas de arquitetura e modelagem](../modeling/what-s-new-for-design-in-visual-studio.md#VersionSupport).

 Para usar um estereótipo, vincule um pacote a um perfil. Isso permite aplicar os estereótipos que são definidos no perfil para os elementos no pacote. Alguns perfis são instalados junto com o Visual Studio. Além disso, você pode definir seus próprios perfis.

 Os estereótipos podem ser definidos na lista de propriedades de um elemento. Para os principais tipos de forma em um diagrama, os estereótipos aplicados também aparecem na forma, conforme mostrado no exemplo.

 ![Uma classe UML com um estereótipo.](../modeling/media/uml-class-stereotype.png "UML_class_stereotype")

> [!NOTE]
> Se você usar um perfil para criar um modelo e, em seguida, compartilhar o modelo com outra pessoa, ele não poderá ver os estereótipos, a menos que eles tenham instalado o mesmo perfil em seu computador.

## <a name="related-topics"></a>Tópicos relacionados

|Título|Descrição|
|-----------|-----------------|
|[Adicionar estereótipos a elementos de modelo UML](../modeling/add-stereotypes-to-uml-model-elements.md)|Colocando um elemento de modelo em um pacote, vinculando o pacote a um perfil e aplicando um estereótipo ao elemento.|
|[Estereótipos padrão para modelos UML](../modeling/standard-stereotypes-for-uml-models.md)|Os perfis padrão UML L2 e L3 são instalados com o Visual Studio e todos os modelos são vinculados a eles por padrão. Eles fornecem estereótipos que você pode usar para anotar seus modelos.<br /><br /> Por exemplo, você pode aplicar o estereótipo «especificação» a uma classe para indicar que ele se destina apenas a definir o comportamento visível externamente de suas instâncias,|
|[Definir um perfil para estender UML](../modeling/define-a-profile-to-extend-uml.md)|Você pode definir seus próprios estereótipos e ferramentas que são adaptados para sua própria área de aplicativo.<br /><br /> Por exemplo, se você desenvolver um software de banco, poderá definir um estereótipo «Account» que possa ser aplicado às classes. Em seguida, você pode usar diagramas de classe para descrever diferentes tipos de conta e suas relações.|
|[Instalar um perfil UML](../modeling/install-a-uml-profile.md)|Se alguém tiver dado a você um perfil de UML, você poderá instalá-lo em seu computador.|
|[Definir um item de caixa de ferramentas de modelagem personalizada](../modeling/define-a-custom-modeling-toolbox-item.md)|Um item de caixa de ferramentas personalizado o salva de uma configuração repetida de um estereótipo em novos elementos.|
