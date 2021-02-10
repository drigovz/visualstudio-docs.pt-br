---
title: Como adicionar o arquivo app.config a um projeto
description: Saiba como adicionar um arquivo de app.config a um projeto C# para que você possa personalizar como o Common Language Runtime Localiza e carrega arquivos de assembly.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- dotnet
ms.openlocfilehash: e9280451d7841755cb3085726843bf6fc1443f8a
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99948277"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Como adicionar um arquivo de configuração de aplicativo a um projeto C#

Ao adicionar um arquivo de configuração de aplicativo (arquivo *app.config*) a um projeto C#, você pode personalizar o modo como o Common Language Runtime localiza e carrega arquivos do assembly. Para saber mais sobre arquivos de configuração de aplicativo, veja [Como o runtime localiza assemblies (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> Os aplicativos da UWP não contêm um arquivo *app.config*.

Quando você cria seu projeto, o ambiente de desenvolvimento copia automaticamente o arquivo *app.config*, altera o nome do arquivo da cópia para corresponder ao executável e, em seguida, move a cópia para o diretório **bin**.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Para adicionar um arquivo de configuração de aplicativo a um projeto C#

1. Na barra de menus, escolha **projeto**  >  **Adicionar novo item**.

     A caixa de diálogo **Adicionar Novo Item** aparecerá.

1. Expanda   >  **itens do Visual C#** instalados e escolha o modelo de **arquivo de configuração de aplicativo** .

1. Na caixa e texto **Nome**, insira um nome e escolha o botão **Adicionar**.

     Um arquivo chamado *app.config* é adicionado ao seu projeto.

## <a name="see-also"></a>Confira também

- [Gerenciar configurações de aplicativo (.NET)](../ide/managing-application-settings-dotnet.md)
- [Esquema do arquivo de configuração (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Configurar aplicativos (.NET Framework)](/dotnet/framework/configure-apps/index)
