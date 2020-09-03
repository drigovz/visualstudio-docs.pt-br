---
title: Como alterar o diretório de saída do build | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
helpviewer_keywords:
- output directory, changing
ms.assetid: a8333c89-afb2-4b1d-b2e2-9146da852402
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: b665f5788d12c294e8ab7f55ecc63d183030a0ca
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72645427"
---
# <a name="how-to-change-the-build-output-directory"></a>Como alterar o diretório de saída do build
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode especificar o local de saída por configuração (para depuração, versão ou ambas) gerada pelo projeto.

> [!NOTE]
> Se você tiver um projeto de **Instalação**, consulte a observação no final deste artigo.

## <a name="changing-the-build-output-directory"></a>Alterando o diretório de saída do build

#### <a name="to-change-the-build-output-directory"></a>Para alterar o diretório de saída do build

1. Na barra de menus, escolha **projeto**, *AppName* **Propriedades**. Você também pode clicar com o botão direito do mouse no nó do projeto no **Gerenciador de Soluções** e selecionar **Propriedades**.

2. Se você tiver um projeto Visual Basic, selecione a guia **Compilar** . Se você tiver um projeto do Visual C#, selecione a guia **Compilar** . Se você tiver um projeto C++ ou um projeto JavaScript, selecione a guia **geral** .

3. Na lista suspensa de configuração na parte superior, escolha a configuração cujo local do arquivo de saída você deseja alterar (depuração, versão ou todos).

     Localize a entrada do caminho de saída (**Caminho de Saída do Build** no Visual Basic, **Diretório de Saída** no Visual C++, **Caminho de Saída** no JavaScript e C#). Especifique um novo diretório de saída de build em relação ao diretório do projeto.

> [!NOTE]
> Em um Projeto de Instalação, a caixa **Nome do arquivo de saída** muda apenas o local do arquivo Setup.exe, não o local dos arquivos de projeto. Para obter mais informações, consulte **compilação, propriedades de configuração, caixa de diálogo Propriedades do projeto de implantação**.

## <a name="see-also"></a>Consulte Também
 [Página de compilação, compilação do projeto (C#)](../ide/reference/build-page-project-designer-csharp.md) [página de propriedades geral (projeto)](https://msdn.microsoft.com/library/593b383c-cd0f-4dcd-ad65-9ec9b4b19c45) [compilando e compilando](../ide/compiling-and-building-in-visual-studio.md)
