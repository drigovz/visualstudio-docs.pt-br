---
title: 'Como: Adicionar uma dependência a um pacote VSIX | Microsoft Docs'
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- package reference
- package assembly
- package dll
- vsix reference
ms.assetid: 8f20177b-dab9-43a3-b959-81a591b451d6
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: f8b350f063c28762edf90edfe71330534451c75d
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711074"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Como: Adicionar uma dependência a um pacote VSIX

Você pode configurar uma implantação de pacote VSIX que instala quaisquer dependências que ainda não estejam presentes no computador de destino. Para isso, inclua as dependências VSIX no arquivo *source.extension.vsixmanifest.*

## <a name="to-add-a-dependency"></a>Para adicionar uma dependência

1. Abra o arquivo *source.extension.vsixmanifest* na exibição **Design.** Vá para a guia **Dependências** e clique em **Novo**.

2. Para adicionar uma extensão instalada: na caixa de diálogo **Adicionar nova dependência,** **selecione Extensão instalada** e, em seguida, para o **Nome,** selecione uma extensão na lista.

3. Para adicionar outro VSIX que não está instalado: na caixa de diálogo **Adicionar nova dependência,** selecione **Arquivo no sistema de arquivos** e, em seguida, use o botão **Procurar** para selecionar o VSIX.

## <a name="require-a-specific-visual-studio-release"></a>Requeira uma versão específica do Visual Studio

Se sua extensão exigir uma versão específica do Visual Studio 2017, por exemplo, ela depende de um recurso lançado em 15.3, você pode especificar o número de compilação em seu VSIX **InstallationTarget**. Por exemplo, a versão 15.3 tem um número de compilação de '15.0.26730.3'. Você pode ver o mapeamento de lançamentos para construir números [aqui.](../install/visual-studio-build-numbers-and-release-dates.md) Observe que o uso do número de versão '15.3' não funcionará corretamente.

Se a sua extensão exigir 15,3 ou mais, você declararia a **Versão De Destino de Instalação** como [15.0.26730.3, 16.0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

O VSIXInstaller detectará versões anteriores do Visual Studio e informará o usuário que uma atualização posterior é necessária.

## <a name="see-also"></a>Confira também

- [Referência do esquema de extensão VSIX 1.0](https://msdn.microsoft.com/library/76e410ec-b1fb-4652-ac98-4a4c52e09a2b)
- [Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Preparar extensões para implantação do Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)
