---
title: Desabilitar a ativação de URL de aplicativos ClickOnce usando o designer
description: Saiba como desabilitar o início automático na instalação para um aplicativo ClickOnce usando o Visual Studio, para que os usuários devam iniciar o aplicativo no menu iniciar.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- disallowURLActivation
- URL activation, ClickOnce applications
- ClickOnce deployment, URL activation
ms.assetid: a337a582-e67c-409a-b52e-607cd1a8fc57
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: c243b0e0565c082e05fd15a1e02aa0507120e16b
ms.sourcegitcommit: 75bfdaab9a8b23a097c1e8538ed1cde404305974
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/07/2020
ms.locfileid: "94350004"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Como desabilitar a ativação de aplicativos ClickOnce pela URL usando o Designer
Normalmente, um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo será iniciado automaticamente imediatamente após ser instalado a partir de um servidor Web. Por motivos de segurança, você pode optar por desabilitar esse comportamento e dizer aos usuários para iniciar o aplicativo no menu **Iniciar** em vez disso. O procedimento a seguir descreve como desabilitar a ativação de URL.

 Essa técnica pode ser usada somente para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos instalados no computador do usuário a partir de um servidor Web. Ele não pode ser usado para aplicativos somente online, que só podem ser iniciados usando sua URL. Para obter mais informações sobre a diferença entre aplicativos instalados e somente online, consulte [escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

 Esse procedimento usa [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] . Você também pode realizar essa tarefa usando o [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)] . Para obter mais informações, consulte [como: desabilitar a ativação de URL de aplicativos ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).

## <a name="procedure"></a>Procedimento

#### <a name="to-disable-url-activation-for-your-application"></a>Para desabilitar a ativação de URL para seu aplicativo

1. Clique com o botão direito do mouse no nome do projeto em **Gerenciador de soluções** e clique em **Propriedades**.

2. Na página **Propriedades** , clique na guia **publicar** .

3. Clique em **Opções**.

4. Clique em **manifestos**.

5. Marque a caixa de seleção rotulada **Bloquear aplicativo para ser ativado por meio de uma URL**.

6. Implante seu aplicativo.

## <a name="see-also"></a>Veja também
- [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)