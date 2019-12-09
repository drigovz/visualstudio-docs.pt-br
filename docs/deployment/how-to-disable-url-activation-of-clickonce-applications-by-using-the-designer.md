---
title: Desabilitar a ativação de URL de aplicativos ClickOnce usando o Designer
ms.date: 11/04/2016
ms.topic: conceptual
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
ms.openlocfilehash: b8296f08c29b3259c19393a860ee34f6c3f05a42
ms.sourcegitcommit: 117ece52507e86c957a5fd4f28d48a0057e1f581
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/28/2019
ms.locfileid: "66263285"
---
# <a name="how-to-disable-url-activation-of-clickonce-applications-by-using-the-designer"></a>Como: Desabilitar a ativação de URL de aplicativos ClickOnce usando o designer
Normalmente, um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo será iniciado automaticamente, imediatamente após a instalação de um servidor Web. Por motivos de segurança, você pode optar por desabilitar esse comportamento e diga aos usuários para iniciar o aplicativo a partir de **iniciar** menu em vez disso. O procedimento a seguir descreve como desabilitar a ativação de URL.

 Essa técnica pode ser usada somente para [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativos instalados no computador do usuário de um servidor Web. Ele não pode ser usado para aplicativos somente online, que podem ser iniciados apenas por meio de sua URL. Para obter mais informações sobre a diferença entre os aplicativos instalados e somente online, consulte [escolhendo uma estratégia de implantação do ClickOnce](../deployment/choosing-a-clickonce-deployment-strategy.md).

 Este procedimento usa [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]. Você também pode realizar essa tarefa usando o [!INCLUDE[winsdklong](../deployment/includes/winsdklong_md.md)]. Para obter mais informações, confira [Como: Desabilitar a ativação de URL de aplicativos ClickOnce](../deployment/how-to-disable-url-activation-of-clickonce-applications.md).

## <a name="procedure"></a>Procedimento

#### <a name="to-disable-url-activation-for-your-application"></a>Para desabilitar a ativação de URL para seu aplicativo

1. Nome do projeto no botão direito do mouse **Gerenciador de soluções**e clique em **propriedades**.

2. Sobre o **propriedades** , clique no **publicar** guia.

3. Clique em **Opções**.

4. Clique em **manifestos**.

5. Selecione a caixa de seleção rotulada **bloquear o aplicativo seja ativado através de uma URL**.

6. Implantar seu aplicativo.

## <a name="see-also"></a>Consulte também
- [Publicando aplicativos ClickOnce](../deployment/publishing-clickonce-applications.md)