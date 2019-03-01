---
title: 'Como: definir uma zona de segurança para um aplicativo ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce deployment, security settings
- code access security, ClickOnce applications
- security zones, ClickOnce applications
ms.assetid: d3dac454-518a-44d7-a76e-ccb7b9c3a150
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: bcb89fea3e364c5933a4b1cfeaf90b44dc14e83d
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56606831"
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>Como definir uma zona de segurança para um aplicativo ClickOnce
Ao definir permissões de segurança para um aplicativo ClickOnce de acesso do código, você precisa para começar com um conjunto básico de permissões na **segurança** página do **Designer de projeto**.

 Na maioria dos casos, você também pode escolher o **Internet** zona que contém um conjunto limitado de permissões, ou o **Intranet Local** zona que contém um conjunto maior de permissões. Se seu aplicativo exigir permissões personalizadas, você pode fazer isso escolhendo os **personalizado** zona de segurança. Para obter mais informações sobre como definir permissões personalizadas, consulte [como: definir permissões personalizadas para um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).

### <a name="to-set-a-security-zone"></a>Para definir uma zona de segurança

1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.

2.  Clique na guia **Segurança**.

3.  Selecione o **Habilitar configurações de segurança do ClickOnce** caixa de seleção.

4.  Selecione o **este é um aplicativo de confiança parcial** botão de opção.

     Os controles na **permissões de segurança do ClickOnce** seção estão habilitados.

5.  No **seu aplicativo será instalado a partir de zona** lista suspensa, selecione uma zona de segurança.

## <a name="see-also"></a>Consulte também
- [Como definir permissões personalizadas para um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Proteger aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)
- [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
