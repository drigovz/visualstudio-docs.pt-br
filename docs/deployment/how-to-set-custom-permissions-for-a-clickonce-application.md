---
title: 'Como: Definir permissões personalizadas para um aplicativo ClickOnce | Microsoft Docs'
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
ms.openlocfilehash: 2c8a6fd6625726f749afcf20b80f83178a47ab92
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63406999"
---
# <a name="how-to-set-custom-permissions-for-a-clickonce-application"></a>Como: Definir permissões personalizadas para um aplicativo ClickOnce
Você pode implantar um [!INCLUDE[ndptecclick](../deployment/includes/ndptecclick_md.md)] aplicativo que usa as permissões padrão para as zonas de Internet ou Intranet Local. Como alternativa, você pode criar uma zona personalizada para as permissões específicas que o aplicativo precisa. Você pode fazer isso ao personalizar as permissões de segurança na **segurança** página do **Designer de projeto**.

### <a name="to-customize-a-permission"></a>Para personalizar uma permissão

1. Com um projeto selecionado no **Gerenciador de Soluções**, no menu **Projeto**, clique em **Propriedades**.

2. Clique na guia **Segurança**.

3. Selecione o **Habilitar configurações de segurança do ClickOnce** caixa de seleção.

4. Selecione o **este é um aplicativo de confiança parcial** botão de opção.

     Os controles na **permissões de segurança do ClickOnce** seção estão habilitados.

5. Dos **seu aplicativo será instalado a partir de zona** lista suspensa, clique em **(personalizada)**.

6. Clique em **Editar XML de permissões**.

     O *manifest* arquivo é aberto no Editor de XML.

7. Antes do `</applicationRequestMinimum>` elemento, adicione o código XML para as permissões que seu aplicativo requer.

    > [!NOTE]
    > Você pode usar o `ToXml` método de uma permissão definida para gerar o código XML para o manifesto do aplicativo. Por exemplo, para gerar o XML para o <xref:System.Security.Permissions.EnvironmentPermission> conjunto de permissões, chame o <xref:System.Security.Permissions.EnvironmentPermission.ToXml%2A> método.

## <a name="see-also"></a>Consulte também
- [Proteger aplicativos ClickOnce](../deployment/securing-clickonce-applications.md)
- [Segurança de acesso do código para aplicativos ClickOnce](../deployment/code-access-security-for-clickonce-applications.md)
