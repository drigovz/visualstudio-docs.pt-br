---
title: Adicionar estereótipos a elementos de modelo UML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-modeling
ms.topic: conceptual
helpviewer_keywords:
- UML model, stereotypes
ms.assetid: 82545252-83ce-4e11-a419-61373be75d16
caps.latest.revision: 17
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 67d489b1446e7205d72b53e160a8c7ca87f216d7
ms.sourcegitcommit: bad28e99214cf62cfbd1222e8cb5ded1997d7ff0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2019
ms.locfileid: "74292335"
---
# <a name="add-stereotypes-to-uml-model-elements"></a>Adicionar estereótipos a elementos de modelo UML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode adicionar um estereótipo a um elemento de modelo UML para anotá-lo e fornecê-lo com propriedades especializadas. Para adicionar um estereótipo a um elemento de modelo, o estereótipo deve ser definido em um perfil e você deve vincular o perfil a um pacote ou ao modelo que contém o elemento de modelo. Cada estereótipo só pode ser adicionado a determinados tipos de elementos de modelo, como classes UML, casos de uso ou componentes.

 Por exemplo, se você quiser definir uma classe UML com o estereótipo «especificação», deverá criá-la em um pacote ou um modelo que esteja vinculado ao padrão do perfil L2.

 Por padrão, cada modelo é vinculado aos perfis padrão UML L2 e L3.

### <a name="to-link-a-profile-to-a-model-or-a-package"></a>Para vincular um perfil a um modelo ou pacote

1. Abra o **Gerenciador de modelos UML**. No menu **arquitetura** , aponte para **Windows**e clique em Gerenciador de **modelos UML**.

2. Localize um pacote ou um modelo que contenha todos os elementos aos quais você deseja aplicar os estereótipos no perfil.

3. Clique com o botão direito do mouse no pacote ou no modelo e clique em **Propriedades**.

4. Na janela **Propriedades** , defina a propriedade **perfis** para os perfis que contêm os estereótipos que você deseja usar.

     Os estereótipos do perfil agora estarão disponíveis em todos os elementos dentro do modelo ou pacote. Se o pacote contiver outros pacotes, os estereótipos também estarão disponíveis nos elementos dentro deles.

### <a name="to-add-stereotypes-to-model-elements-or-relationships"></a>Para adicionar estereótipos a elementos ou relações de modelo

1. Clique com o botão direito do mouse no elemento de modelo ou na relação, em um diagrama ou em um **Gerenciador de modelos UML**, e clique em **Propriedades**.

    > [!NOTE]
    > Para adicionar os mesmos estereótipos a vários elementos, você pode selecionar vários elementos e clicar com o botão direito do mouse em um deles.

2. Clique na propriedade **estereótipos** e selecione os estereótipos que você deseja aplicar.

     Os estereótipos selecionados aparecem dentro de «divisas» no elemento de modelo, para a maioria dos tipos de elemento e relação.

    > [!NOTE]
    > Se você não puder ver a propriedade **estereótipos** ou se o estereótipo desejado não for exibido, verifique se o elemento de modelo está dentro de um pacote ou um modelo ao qual o perfil apropriado foi vinculado.

3. Alguns estereótipos permitem que você defina os valores de propriedades adicionais para o elemento de modelo. Para ver essas propriedades, expanda a propriedade **estereótipos** .

### <a name="to-create-model-elements-within-a-package"></a>Para criar elementos de modelo dentro de um pacote

1. Crie um pacote em um diagrama de classes UML ou no **Gerenciador de modelos UML**.

2. Adicione elementos de modelo ao pacote de uma das seguintes maneiras:

    - Em um diagrama de classes UML, clique na ferramenta de um elemento e, em seguida, clique dentro do pacote no diagrama.

         \- ou -

    - No Gerenciador de modelos UML, clique com o botão direito do mouse no pacote, aponte para **Adicionar**e clique em um tipo de elemento.

         \- ou -

    - No Gerenciador de modelos UML, arraste um elemento existente para o pacote.

         \- ou -

    - Vincule um diagrama ao pacote e, em seguida, crie elementos dentro do diagrama.

         Para fazer isso, clique com o botão direito do mouse em uma parte em branco do diagrama e clique em **Propriedades**. Na janela **Propriedades** , defina **pacote vinculado** para o pacote desejado.

         Todos os novos elementos que você criar no diagrama serão definidos dentro desse pacote.

         Você pode fazer isso somente com alguns tipos de diagrama.

## <a name="see-also"></a>Consulte também
 [Definir um perfil para estender UML](../modeling/define-a-profile-to-extend-uml.md) [Personalize seu modelo com perfis e estereótipos](../modeling/customize-your-model-with-profiles-and-stereotypes.md) [definir pacotes e namespaces](../modeling/define-packages-and-namespaces.md)

