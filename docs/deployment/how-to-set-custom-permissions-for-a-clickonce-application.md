---
title: 'Como: definir permissões personalizadas para um aplicativo ClickOnce | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
helpviewer_keywords:
- ClickOnce applications, permissions
- permissions, ClickOnce applications
ms.assetid: 660459ca-ef73-44a8-b323-610001f63b93
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: cc400b4e9b504b512fc8ed3ec6c6dec3e676310e
ms.sourcegitcommit: d0425b6b7d4b99e17ca6ac0671282bc718f80910
ms.translationtype: MTE95
ms.contentlocale: pt-BR
ms.lasthandoff: 02/21/2019
ms.locfileid: "56630659"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Como definir permissões personalizadas para um aplicativo ClickOnce
Você pode implantar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo que usa as permissões padrão para as zonas de Internet ou Intranet Local. Como alternativa, você pode criar uma zona personalizada para as permissões específicas que o aplicativo precisa. Você pode fazer isso ao personalizar as permissões de segurança na **segurança** página do **Designer de projeto**.

### <a name="to-customize-a-permission"></a>Para personalizar uma permissão

1.  Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.

2.  Clique na guia **Segurança**.

3.  Selecione o **Habilitar configurações de segurança do ClickOnce** caixa de seleção.

4.  Selecione o **este é um aplicativo de confiança parcial** botão de opção.

     Os controles na **permissões de segurança do ClickOnce** seção estão habilitados.

5.  Dos **seu aplicativo será instalado a partir de zona** lista suspensa, clique em **(personalizada)**.

6.  Clique em **Editar XML de permissões**.

     O *manifest* arquivo é aberto no Editor de XML.

7.  Antes do `</applicationRequestMinimum>` elemento, adicione o código XML para as permissões que seu aplicativo requer.

    > [!NOTE]
    >  Você pode usar o `ToXml` método de uma permissão definida para gerar o código XML para o manifesto do aplicativo. Por exemplo, para gerar o XML para o <xref:System.Security.Permissions.EnvironmentPermission> conjunto de permissões, chame o <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> método.

## <a name="see-also"></a>Consulte também
- [Proteger aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)
- [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
