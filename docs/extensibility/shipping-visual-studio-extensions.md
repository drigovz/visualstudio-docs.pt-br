---
title: Expedição Visual Studio Extensões | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSIX deployment
- deployment, VSIX
- satellite DLLs, in VSIX packages
ms.assetid: 13cd263d-25f7-488e-9c1a-cff908caedb6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 767bb24bb5cb47f1af1452aa04ebdc91c778e284
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80700121"
---
# <a name="shipping-visual-studio-extensions"></a>Enviando extensões do Visual Studio
Depois de terminar de desenvolver sua extensão, você pode instalá-la em outras máquinas, compartilhá-la com seus amigos e colegas de trabalho ou publicá-la no Visual Studio Marketplace. Nesta seção explicamos todas as coisas que você precisa fazer para publicar e manter sua extensão: trabalhar com arquivos .vsix, publicação, localização e atualização.

## <a name="working-with-vsix-extensions"></a>Trabalhando com extensões VSIX
 Você pode criar uma extensão VSIX criando um Projeto VSIX em branco e, em seguida, adicionando diferentes modelos de itens a ele. Para obter mais informações, consulte [VSIX Project Template](../extensibility/vsix-project-template.md).

 Você pode usar o formato VSIX para empacotar modelos de projeto, modelos de itens, VSPackages, componentes MEF (Managed Extensibility Framework, **Controls Toolbox,** conjuntos e tipos personalizados) (isso inclui páginas iniciais personalizadas para o Visual Studio 2017). O formato VSIX usa implantação baseada em arquivos. Para obter mais informações sobre os pacotes VSIX, consulte [Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md).

 O formato VSIX não suporta a instalação de trechos de código. Também não suporta certos outros cenários, como escrever para o Global Assembly Cache (GAC) ou para o registro do sistema. Se você precisar escrever para o GAC ou para o registro na instalação, você deve usar o Instalador do Windows. Para obter mais informações, consulte [Preparando extensões para implantação do instalador do Windows](../extensibility/preparing-extensions-for-windows-installer-deployment.md).

## <a name="publishing-your-extension-to-the-visual-studio-marketplace"></a>Publicando sua extensão para o Visual Studio Marketplace
 Você pode distribuir sua extensão para outras pessoas simplesmente enviando-lhes o arquivo .vsix ou colocando em um servidor. Mas a melhor maneira de colocar seu código nas mãos de muita gente é colocá-lo no [Visual Studio Marketplace.](https://marketplace.visualstudio.com/vs) As extensões do Visual Studio Marketplace estão disponíveis para os usuários do Visual Studio através **de Extensões e Atualizações**. Para obter mais informações, consulte [Encontrar e Usar extensões do Visual Studio](../ide/finding-and-using-visual-studio-extensions.md).

 Para um exemplo completo que mostra como carregar uma extensão no Visual Studio Marketplace, consulte [Passo a Passo: Publicar uma extensão do Visual Studio](../extensibility/walkthrough-publishing-a-visual-studio-extension.md).

## <a name="private-galleries"></a>Galerias privadas
 À medida que você desenvolve controles, modelos e ferramentas, você pode compartilhá-los com sua organização postando-os em uma galeria privada em sua intranet. Para obter mais informações, consulte [Galerias Privadas](../extensibility/private-galleries.md).

## <a name="localizing-your-extension"></a>Localizando sua extensão
 Se você está planejando liberar sua extensão em diferentes locais, você deve considerar localizá-la. Para obter uma explicação do que está envolvido, consulte [Localizing VSIX Packages](../extensibility/localizing-vsix-packages.md).

## <a name="updating-and-versioning-your-extension"></a>Atualizando e versão de sua extensão
 Depois de publicar sua extensão, chegará um momento em que você precisará atualizá-la. Para saber como atualizar uma extensão que foi publicada no Visual Studio Marketplace, consulte [Como: Atualizar uma extensão](../extensibility/how-to-update-a-visual-studio-extension.md).

 Você pode definir sua extensão para suportar várias versões do Visual Studio. Para obter mais informações, consulte [Suporte a várias versões do Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md).

## <a name="related-topics"></a>Tópicos Relacionados

|Title|Descrição|
|-----------|-----------------|
|[Introdução ao modelo de projeto do VSIX](../extensibility/getting-started-with-the-vsix-project-template.md)|Explica como usar o modelo de projeto VSIX para instalar um modelo de projeto personalizado.|
|[Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md)|Descreve os componentes de um pacote VSIX.|
|[Modelo de projeto VSIX](../extensibility/vsix-project-template.md)|Fornece instruções passo a passo sobre como empacotar e publicar uma extensão.|
|[Localizar pacotes VSIX](../extensibility/localizing-vsix-packages.md)|Explica como fornecer texto localizado para o processo de instalação usando arquivos extension.vsixlangpack.|
|[Como atualizar uma extensão](../extensibility/how-to-update-a-visual-studio-extension.md)|Descreve como atualizar uma extensão em seu sistema e como implantar uma atualização em uma extensão do Visual Studio existente.|
|[Como adicionar uma dependência a um pacote VSIX](../extensibility/how-to-add-a-dependency-to-a-vsix-package.md)|Descreve como adicionar referências aos pacotes de implantação vsix.|
|[Preparando extensões para a implantação do Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)|Explica como implantar sua extensão no Windows Installer.|
|[Assinando pacotes VSIX](../extensibility/signing-vsix-packages.md)|Explica como assinar pacotes VSIX.|
|[Galerias privadas](../extensibility/private-galleries.md)|Explica como criar galerias privadas para extensões.|
|[Fornecer suporte à várias versões do Visual Studio](../extensibility/supporting-multiple-versions-of-visual-studio.md)|Mostra como ter sua extensão suportando várias versões do Visual Studio.|
|[Localizando o Visual Studio](locating-visual-studio.md)|Descreve como localizar instâncias do Visual Studio para implantação de extensão personalizada.|
