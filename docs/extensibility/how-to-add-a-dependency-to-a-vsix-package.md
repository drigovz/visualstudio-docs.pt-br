---
title: 'Como: adicionar uma dependência a um pacote VSIX | Microsoft Docs'
description: Saiba como configurar uma implantação de pacote VSIX que instala quaisquer dependências que ainda não estão presentes no computador de destino.
ms.custom: SEO-VS-2020
ms.date: 11/04/2016
ms.topic: how-to
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
ms.openlocfilehash: d7ef19bafd0788ed15094979141679625e4e992f
ms.sourcegitcommit: d10f37dfdba5d826e7451260c8370fd1efa2c4e4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2020
ms.locfileid: "96993829"
---
# <a name="how-to-add-a-dependency-to-a-vsix-package"></a>Como: adicionar uma dependência a um pacote VSIX

Você pode configurar uma implantação de pacote VSIX que instala quaisquer dependências que ainda não estão presentes no computador de destino. Para fazer isso, inclua as dependências do VSIX no arquivo *Source. Extension. vsixmanifest* .

## <a name="to-add-a-dependency"></a>Para adicionar uma dependência

1. Abra o arquivo *Source. Extension. vsixmanifest* no modo de exibição de **design** . Vá para a guia **dependências** e clique em **novo**.

2. Para adicionar uma extensão instalada: na caixa de diálogo **Adicionar nova dependência** , selecione a **extensão instalada** e, em seguida, para o **nome**, selecione uma extensão na lista.

3. Para adicionar outro VSIX que não está instalado: na caixa de diálogo **Adicionar nova dependência** , selecione **arquivo no sistema de arquivos** e, em seguida, use o botão **procurar** para selecionar o VSIX.

## <a name="require-a-specific-visual-studio-release"></a>Exigir uma versão específica do Visual Studio

Se sua extensão exigir uma versão específica do Visual Studio 2017, por exemplo, depende de um recurso lançado em 15,3, você poderá especificar o número de Build em seu **INSTALLATIONTARGET** VSIX. Por exemplo, a versão 15,3 tem um número de Build de ' 15.0.26730.3 '. Você pode ver o mapeamento de liberações para criar números [aqui](../install/visual-studio-build-numbers-and-release-dates.md). Observe que o uso do número de versão ' 15,3 ' não funcionará corretamente.

Se sua extensão exigir 15,3 ou superior, você declararia a **versão InstallationTarget** como [15.0.26730.3, 16,0):

```xml
<Installation>
  <InstallationTarget Id="Microsoft.VisualStudio.Community" Version="[15.0.26730.3, 16.0)" />
</Installation>
```

O VSIXInstaller irá detectar versões anteriores do Visual Studio e informar ao usuário que uma atualização posterior é necessária.

## <a name="see-also"></a>Confira também

- [Referência do esquema de extensão do VSIX 1,0](/previous-versions/dd393700(v=vs.110))
- [Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md)
- [Preparar extensões para implantação de Windows Installer](../extensibility/preparing-extensions-for-windows-installer-deployment.md)