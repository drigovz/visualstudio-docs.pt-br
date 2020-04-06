---
title: 'Como: Atualizar uma extensão do Visual Studio | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- update package
- update extension
- new package version
ms.assetid: 93f79774-7b79-4dd6-94ad-13698f72c257
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 266c0a49db1bca03cec0eb68301445102173df3d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80710661"
---
# <a name="how-to-update-a-visual-studio-extension"></a>Como: Atualizar uma extensão do Visual Studio
Você pode atualizar uma extensão do Visual Studio em seu sistema usando **Extensões e Atualizações** para instalar a versão atualizada. Se você criar uma versão atualizada de uma extensão, você pode assiná-la como atualizada incrementando o número da versão no manifesto VSIX.

 As atualizações são instaladas quando o manifesto VSIX `ID` da extensão de `Version` entrada tem o mesmo que o instalado e um número maior. Se `Version` o número for o mesmo ou inferior, o pacote não poderá ser instalado. Se `ID` os valores não corresponderem, o pacote que ainda não está instalado é reconhecido como uma extensão separada.

 Para ajudar a evitar conflitos durante o desenvolvimento, recomendamos que você desinstale versões anteriores de extensões em andamento e também desinstale ou desative quaisquer outras extensões potencialmente conflitantes.

## <a name="to-update-an-extension-on-your-system"></a>Para atualizar uma extensão em seu sistema

1. No menu **Ferramentas**, clique em **Extensões e Atualizações**.

2. No painel esquerdo, clique em **Atualizações**.

3. No painel do meio, clique na atualização que deseja instalar.

     O número da versão da extensão atualizada é exibido no painel direito, juntamente com outras informações.

4. Na parte inferior do painel direito, clique em **Atualizar**.

## <a name="to-publish-an-update-of-an-extension"></a>Para publicar uma atualização de uma extensão

1. No Visual Studio, abra a solução para a extensão que deseja atualizar. Faça as mudanças.

    > [!IMPORTANT]
    > Todas as extensões do usuário não são atualizadas automaticamente. Você deve sempre assinar suas extensões.

2. Em **Solution Explorer,** open *source.extension.manifest*.

3. No designer manifesto, aumente o valor do número no campo **Versão.**

4. Salve a solução e construa-a.

5. Carregue o novo arquivo *.vsix* (na pasta\* *\bin\Debug do projeto) para o site [do Visual Studio Marketplace.](https://marketplace.visualstudio.com/vs)

     Quando um usuário que tem uma versão anterior da extensão abre **Extensões e Atualizações,** a nova versão aparecerá na lista **Atualizações,** desde que a ferramenta esteja configurada para procurar automaticamente atualizações.

     Você pode ativar ou desativar a verificação automática para obter atualizações na parte inferior do painel **Atualizações** (**Habilitar/desativar a detecção automática de atualizações disponíveis**), o que altera a configuração **check for updates** in **Tools** > **Options** > **Environment** > **Extensions and Updates**.

    > [!NOTE]
    > A partir da Atualização 2 do Visual Studio 2015, você pode especificar (em **Tools** > **Options** > **Environment** > **Extensions and Updates**) se você deseja atualizações automáticas para extensões por usuário, todas as extensões do usuário ou ambas (a configuração padrão).

## <a name="see-also"></a>Confira também
- [Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Encontre e use extensões do Visual Studio](../ide/finding-and-using-visual-studio-extensions.md)
