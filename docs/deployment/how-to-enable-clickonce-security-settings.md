---
title: 'Como: Habilitar configurações de segurança do ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- security [Visual Studio], ClickOnce applications
- ClickOnce deployment, security settings
- security settings, ClickOnce deployment
ms.assetid: 73cd3e9d-cd72-4ad2-8cae-94d6bb6b01e0
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f89db12596754630eddaf78b9429eb2983625481
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56599825"
---
# <a name="how-to-enable-clickonce-security-settings"></a>Como habilitar configurações de segurança do ClickOnce
Segurança de acesso do código para aplicativos ClickOnce deve ser habilitada para publicar o aplicativo. Isso é feito automaticamente quando você publica um aplicativo usando o Assistente de publicação.

 Em alguns casos, habilitar a segurança de acesso do código pode afetar o desempenho ao compilar ou depurar seu aplicativo. Nesses casos, convém desabilitar temporariamente as configurações de segurança.

 Configurações de segurança do ClickOnce podem ser habilitadas ou desabilitadas na **segurança** página do **Designer de projeto**.

### <a name="to-enable-clickonce-security-settings"></a>Para habilitar as configurações de segurança do ClickOnce

1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.

2.  Clique na guia **Segurança**.

3.  Selecione o **Habilitar configurações de segurança do ClickOnce** caixa de seleção.

     Agora você pode personalizar as configurações de segurança para seu aplicativo na página de segurança.

    > [!NOTE]
    >  Essa caixa de seleção é selecionada automaticamente cada vez que o aplicativo é publicado com o **publicar** assistente.

### <a name="to-disable-clickonce-security-settings"></a>Para desabilitar as configurações de segurança do ClickOnce

1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.

2.  Clique na guia **Segurança**.

3.  Desmarque a **Habilitar configurações de segurança do ClickOnce** caixa de seleção.

     O aplicativo será executado com as configurações de segurança de confiança total; todas as configurações de **segurança** página será ignorada.

    > [!NOTE]
    >  Cada vez que o aplicativo é publicado com o Assistente de publicação, essa caixa de seleção será selecionada; Você deverá desmarcá-la novamente depois de cada publicação bem-sucedida.

## <a name="see-also"></a>Consulte também
- [Proteger aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)
- [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
