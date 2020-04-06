---
title: 'Passo a passo: Criando um Editor Personalizado | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- editors [Visual Studio SDK], custom - create
ms.assetid: d090abb6-d99f-4083-a3db-cd16bf81ce7d
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7eb376637fd72f3856415ee2527ec622fea02950
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697688"
---
# <a name="walkthrough-create-a-custom-editor"></a>Passo a passo: Crie um editor personalizado
O modelo de projeto VSPackage pode criar um editor personalizado simples no C++. O modelo de projeto VSPackage não suporta mais projetos C# ou Visual Basic. Para obter mais informações, consulte [Visual Studio SDK](../extensibility/visual-studio-sdk.md).

## <a name="prerequisites"></a>Pré-requisitos
 Para acompanhar este passo a passo, você deve instalar o Visual Studio SDK. Para obter mais informações, consulte [Instalar o Visual Studio SDK](../extensibility/installing-the-visual-studio-sdk.md).

## <a name="the-visual-studio-package-project-template"></a>O modelo de projeto do Visual Studio Package
 Você pode encontrar o modelo de projeto visual studio package na caixa de diálogo **Novo Projeto** sob a pasta **C++ Extensibility.**

### <a name="to-create-a-vspackage-using-the-visual-studio-package-template"></a>Para criar um VSPackage usando o modelo de pacote do Visual Studio

1. Crie um projeto com o modelo visual studio package.

2. Selecione a opção **Editor personalizado** e clique **em Next**. A **página Opções de editor** aparece.

3. Digite o nome do seu editor na caixa Nome do **editor.** Digite a extensão de arquivo que deseja ser associada ao seu editor na caixa **Extensão de arquivo.** Seu editor está disponível para arquivos com esta extensão. A extensão de arquivo está registrada apenas para o Visual Studio, não para o Windows. Digite o nome do arquivo padrão para novos documentos criados com seu editor na caixa **Nome de arquivo** padrão.

4. Clique **em Concluir** para criar seu VSPackage na pasta especificada.

### <a name="to-test-your-custom-editor"></a>Para testar seu editor personalizado

1. No **menu Arquivo,** aponte para **Novo** e clique **em Arquivo**.

2. No painel **Modelos Instalados** da caixa de diálogo **Arquivo Novo,** selecione o modelo de arquivo e, em seguida, o tipo de arquivo registrado.

3. Clique **em Abrir** para visualizar e editar o documento.

     O editor suporta operações de corte e cola, de encontrar e substituir e abrir e carregar.

## <a name="see-also"></a>Confira também
- [VSPackages](../extensibility/internals/vspackages.md)
