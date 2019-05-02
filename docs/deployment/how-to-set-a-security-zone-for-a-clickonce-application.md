---
title: 'Como: Definir uma zona de segurança para um aplicativo ClickOnce | Microsoft Docs'
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
ms.openlocfilehash: 31a61dd337fce614c1271f994a42ec90f3be8acb
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62898383"
---
# <a name="how-to-set-a-security-zone-for-a-clickonce-application"></a>Como: Definir uma zona de segurança para um aplicativo ClickOnce
Ao definir permissões de segurança para um aplicativo ClickOnce de acesso do código, você precisa para começar com um conjunto básico de permissões na **segurança** página do **Designer de projeto**.

 Na maioria dos casos, você também pode escolher o **Internet** zona que contém um conjunto limitado de permissões, ou o **Intranet Local** zona que contém um conjunto maior de permissões. Se seu aplicativo exigir permissões personalizadas, você pode fazer isso escolhendo os **personalizado** zona de segurança. Para obter mais informações sobre como definir permissões personalizadas, consulte [como: Definir permissões personalizadas para um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md).

### <a name="to-set-a-security-zone"></a>Para definir uma zona de segurança

1. Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.

2. Clique na guia **Segurança**.

3. Selecione o **Habilitar configurações de segurança do ClickOnce** caixa de seleção.

4. Selecione o **este é um aplicativo de confiança parcial** botão de opção.

     Os controles na **permissões de segurança do ClickOnce** seção estão habilitados.

5. No **seu aplicativo será instalado a partir de zona** lista suspensa, selecione uma zona de segurança.

## <a name="see-also"></a>Consulte também
- [Como: Definir permissões personalizadas para um aplicativo ClickOnce](../deployment/how-to-set-custom-permissions-for-a-clickonce-application.md)
- [Proteger aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)
- [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
