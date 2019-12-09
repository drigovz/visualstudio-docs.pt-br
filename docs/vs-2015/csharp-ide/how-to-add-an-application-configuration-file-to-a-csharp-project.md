---
title: 'Como: adicionar um arquivo de configuração de aplicativo a C# um projeto | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
dev_langs:
- CSharp
helpviewer_keywords:
- app.config files, adding to C# projects
ms.assetid: 9caf6bb0-c2fc-4ab6-ba69-bed3b880fbf8
caps.latest.revision: 20
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f8417b5520dc9587fa3231a3bc459335d2a9896d
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72667529"
---
# <a name="how-to-add-an-application-configuration-file-to-a-c-project"></a>Como adicionar um Arquivo de Configuração do Aplicativo a um projeto C#
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Ao adicionar um arquivo de configuração de aplicativo (arquivo app.config) a um projeto C#, você pode personalizar o modo como o Common Language Runtime localiza e carrega arquivos do assembly. Para obter mais informações sobre arquivos de configuração de aplicativo, consulte [como o tempo de execução localiza assemblies](https://msdn.microsoft.com/library/772ac6f4-64d2-4cfb-92fd-58096dcd6c34).

> [!NOTE]
> A Windows Store não dá suporte a <xref:System.Configuration>. Como resultado, os aplicativos da loja não contêm um modelo app. config.

 Quando você cria seu projeto, o ambiente de desenvolvimento copia automaticamente o arquivo app. config, altera o nome do arquivo da cópia para corresponder ao seu executável e, em seguida, move a cópia para o diretório bin.

### <a name="to-add-an-application-configuration-file-to-your-c-project"></a>Para adicionar um arquivo de configuração do aplicativo ao projeto C#

1. Na barra de menus, escolha **projeto**, **Adicionar novo item**.

     A caixa de diálogo **Adicionar Novo Item** é exibida.

2. Expanda **instalado**, expanda **itens visuais C#** e escolha o modelo de **arquivo de configuração de aplicativo** .

3. Na caixa e texto **Nome**, insira um nome e escolha o botão **Adicionar**.

     Um arquivo chamado App. config é adicionado ao seu projeto.

## <a name="see-also"></a>Consulte também
 [Gerenciando configurações de aplicativo (.net)](../ide/managing-application-settings-dotnet.md) [configuração de esquema de arquivo](https://msdn.microsoft.com/library/69003d39-dc8a-460c-a6be-e6d93e690b38) [configurar aplicativos](https://msdn.microsoft.com/library/86bd26d3-737e-4484-9782-19b17f34cd1f) [como: configurar um aplicativo para direcionar uma versão .NET Framework](https://msdn.microsoft.com/5247b307-89ca-417b-8dd0-e8f9bd2f4717) [usando o ambiente C# de desenvolvimento do Visual Studio para](../csharp-ide/using-the-visual-studio-development-environment-for-csharp.md)