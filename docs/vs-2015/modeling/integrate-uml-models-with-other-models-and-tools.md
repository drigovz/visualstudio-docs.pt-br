---
title: Integre modelos UML a outros modelos e ferramentas | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML - extending, references to models
ms.assetid: 9e75e7d1-93cf-4196-baa3-bd10b9af16d3
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 72ea0c562bb9c2a8050fc1365fac19df20232f80
ms.sourcegitcommit: 939407118f978162a590379997cb33076c57a707
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/13/2020
ms.locfileid: "75918360"
---
# <a name="integrate-uml-models-with-other-models-and-tools"></a>Integrar modelos UML a outros modelos e ferramentas
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Os modelos UML podem ser integrados a outros modelos e a linguagens específicas de domínio.

 Você pode integrar modelos das seguintes maneiras escrevendo o código de extensão para executar uma variedade de funções:

 Anexe referências de qualquer elemento a outros itens, como arquivos ou elementos em outros modelos.
Em um elemento UML, você pode armazenar links para outros elementos, arquivos ou outros objetos UML, codificando suas identidades como cadeias de caracteres.

 Por exemplo, você poderia escrever uma extensão que possa vincular qualquer ação UML (ou seja, um elemento em um diagrama de atividade) a outro diagrama de atividade. Quando o usuário clica duas vezes na ação, o outro diagrama é aberto. Isso permite que o usuário forneça uma exibição mais detalhada da ação.

 Há duas maneiras pelas quais você pode armazenar cadeias de caracteres e outros dados em qualquer elemento:

- **Propriedades de estereótipo.** Você pode definir um perfil UML, no qual você define um estereótipo que adiciona propriedades a tipos especificados de elemento UML. Por exemplo, você pode definir um perfil que adiciona uma propriedade chamada **MoreDetail** a uma ação UML. Você poderia escrever o código de extensão que armazena dados de link em uma ação aplicando o estereótipo à ação e, em seguida, armazenando os dados na propriedade.

   O estereótipo e suas propriedades são visíveis para o usuário na janela Propriedades.

   Para implantar essa extensão, você empacotaria a definição de perfil e o código de extensão em uma única extensão de [!INCLUDE[vsprvs](../includes/vsprvs-md.md)].

   Para obter mais informações, consulte [definir um perfil para estender o UML](../modeling/define-a-profile-to-extend-uml.md).

- **Referências.** Você pode anexar um conjunto de cadeias de caracteres a qualquer elemento UML. Você poderia escrever um código que armazene as informações como um nome de arquivo ou o GUID de outro elemento. Isso pode ser feito sem fornecer definições adicionais. As referências não são visíveis diretamente para o usuário.

Há duas maneiras de codificar referências a elementos de modelo:

- **GUID e nome do arquivo** do elemento de modelo de destino e o modelo que o contém, ou um diagrama específico que o exibe.

- **Referências de ModelBus.** ModelBus é uma estrutura para criar e resolver referências entre modelos. Ele inclui o seletor ModelBus, que permite ao usuário selecionar um elemento em um modelo. Ele também ajuda o usuário a resolver referências que são perdidas devido a alterações no modelo de destino.

   Para obter mais informações, consulte [integrando modelos usando o Visual Studio ModelBus](../modeling/integrating-models-by-using-visual-studio-modelbus.md).

  Propagar alterações de um modelo para outro.
  Por exemplo, você pode sincronizar o nome de um elemento com o nome do diagrama vinculado, de modo que, se o usuário alterar um, o outro também será alterado. Há dois mecanismos para fazer isso:

1. **As regras VMSDK** podem ser usadas para propagar alterações dentro do mesmo modelo.

2. **Eventos VMSDK** podem ser usados para propagar alterações fora do modelo – por exemplo, para alterar o nome de arquivo de um documento vinculado ou para alterar um elemento em outro modelo.

   Para obter informações sobre esses dois mecanismos, consulte [como: responder a alterações em um modelo UML](../misc/how-to-respond-to-changes-in-a-uml-model.md).

   Arraste os elementos para copiá-los de um modelo para outro você pode permitir que o usuário crie elementos arrastando itens para um diagrama UML. O elemento criado não precisa ser uma cópia do original. Por exemplo, você pode permitir que o usuário arraste um diagrama de atividade do Gerenciador de soluções para outro diagrama de atividade, para criar uma nova ação.

   Para obter mais informações, consulte [definir um manipulador de gestos em um diagrama de modelagem](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) e [como adicionar um manipulador de arrastar e soltar](../modeling/how-to-add-a-drag-and-drop-handler.md).

## <a name="see-also"></a>Veja também
 [Definir um comando de menu em um diagrama de modelagem](../modeling/define-a-menu-command-on-a-modeling-diagram.md) [definir um manipulador de gestos em um diagrama de modelagem](../modeling/define-a-gesture-handler-on-a-modeling-diagram.md) [como: adicionar um manipulador de arrastar e soltar](../modeling/how-to-add-a-drag-and-drop-handler.md) [como: responder a alterações em um modelo UML](../misc/how-to-respond-to-changes-in-a-uml-model.md)
