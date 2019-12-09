---
title: Como adicionar o arquivo app.config a um projeto
ms.date: 11/04/2016
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- dotnet
ms.openlocfilehash: 48e6516b48b524c3da4d80bc5171608ac1aea03d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72654258"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Como adicionar um arquivo de configuração de aplicativo a um projeto C#

Ao adicionar um arquivo de configuração de aplicativo (arquivo *app.config*) a um projeto C#, você pode personalizar o modo como o Common Language Runtime localiza e carrega arquivos do assembly. Para saber mais sobre arquivos de configuração de aplicativo, veja [Como o tempo de execução localiza assemblies (.NET Framework)](/dotnet/framework/deployment/how-the-runtime-locates-assemblies).

> [!NOTE]
> Os aplicativos da UWP não contêm um arquivo *app.config*.

Quando você cria seu projeto, o ambiente de desenvolvimento copia automaticamente o arquivo *app.config*, altera o nome do arquivo da cópia para corresponder ao executável e, em seguida, move a cópia para o diretório **bin**.

## <a name="to-add-an-application-configuration-file-to-a-c-project"></a>Para adicionar um arquivo de configuração de aplicativo a um projeto C#

1. Na barra de menus, escolha **Projeto** > **Adicionar Novo Item**.

     A caixa de diálogo **Adicionar Novo Item** é exibida.

1. Expanda **Instalado** > **Itens do Visual C#** e, em seguida, escolha o modelo **Arquivo de Configuração de Aplicativo**.

1. Na caixa e texto **Nome**, insira um nome e escolha o botão **Adicionar**.

     Um arquivo chamado *app.config* é adicionado ao seu projeto.

## <a name="see-also"></a>Consulte também

- [Gerenciar configurações do aplicativo (.NET)](../ide/managing-application-settings-dotnet.md)
- [Esquema do arquivo de configuração (.NET Framework)](/dotnet/framework/configure-apps/file-schema/index)
- [Configurar aplicativos (.NET Framework)](/dotnet/framework/configure-apps/index)