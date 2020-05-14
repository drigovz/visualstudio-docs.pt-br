---
title: Preparando extensões para implantação do instalador do Windows | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- vsix msi
ms.assetid: 5ee2d1ba-478a-4cb7-898f-c3b4b2ee834e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 8636dfbbad06192e5edbb61a9a784f64b8f3f14f
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80702023"
---
# <a name="prepare-extensions-for-windows-installer-deployment"></a>Preparar extensões para implantação do Windows Installer
Não é possível usar um pacote do Windows Installer (MSI) para implantar um pacote VSIX. No entanto, você pode extrair o conteúdo de um pacote VSIX para implantação do MSI. Este documento mostra como preparar um projeto cuja saída padrão é um pacote VSIX para inclusão em um projeto de configuração.

## <a name="prepare-an-extension-project-for-windows-installer-deployment"></a>Prepare um projeto de extensão para implantação do Windows Installer
 Execute essas etapas em novos projetos de extensão antes de adicionar a um projeto de configuração.

### <a name="to-prepare-an-extension-project-for-windows-installer-deployment"></a>Para preparar um projeto de extensão para implantação do Windows Installer

1. Crie um vsPackage, componente MEF, Adornmento de Editor ou outro tipo de projeto de extensibilidade que inclua um manifesto VSIX.

2. Abra o manifesto VSIX no editor de código.

3. Defina `InstalledByMsi` o elemento do `true`manifesto VSIX para . Para obter mais informações sobre o manifesto VSIX, consulte [o esquema de extensão VSIX 2.0](../extensibility/vsix-extension-schema-2-0-reference.md).

     Isso impede que o instalador VSIX tente instalar o componente.

4. Clique com o botão direito do mouse no projeto no **Solution Explorer** e clique em **Propriedades**.

5. Selecione a guia **VSIX.**

6. Verifique a caixa rotulada **como conteúdo Copy VSIX para o seguinte local** e digite o caminho para onde o projeto de configuração irá pegar os arquivos.

## <a name="extract-files-from-an-existing-vsix-package"></a>Extrair arquivos de um pacote VSIX existente
 Execute essas etapas para adicionar o conteúdo de um pacote VSIX existente a um projeto de configuração quando você não tiver os arquivos de origem.

### <a name="to-extract-files-from-an-existing-vsix-package"></a>Para extrair arquivos de um pacote VSIX existente

1. Renomeie o *. Arquivo VSIX* contendo a extensão de *filename.vsix* para *filename.zip*.

2. Copie o conteúdo do arquivo *.zip* em um diretório.

3. Exclua o arquivo *[Content_types].xml* do diretório.

4. Editar o manifesto VSIX, como mostrado no procedimento anterior.

5. Adicione os arquivos restantes ao projeto de configuração.

## <a name="see-also"></a>Confira também
- [Implantação do instalador do Visual Studio](https://msdn.microsoft.com/library/121be21b-b916-43e2-8f10-8b080516d2a0)
- [Passo a passo: Crie uma ação personalizada](/previous-versions/visualstudio/visual-studio-2010/d9k65z2d(v=vs.100))
