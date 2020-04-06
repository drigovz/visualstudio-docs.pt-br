---
title: VSIX Manifest Designer | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- VS.Sdk.VsixManifestEditor
helpviewer_keywords:
- vsixmanifest
- vsix manifest
- manifest designer
ms.assetid: 5a691e77-cf91-430d-90ea-361d9031ef83
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30620e0fe91d0e90995d2d2f721950f878c65fdc
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80697893"
---
# <a name="vsix-manifest-designer"></a>Designer de manifesto do VSIX
Modifica um arquivo manifesto de pacote VSIX, que define o comportamento de instalação de uma extensão do Visual Studio.

 O **VSIX Manifest Designer** mapeia o esquema VSIX subjacente. Cada elemento no esquema pode ser definido usando um controle correspondente no designer. Para obter mais informações sobre o esquema, consulte [VSIX Extension Schema 2.0 Reference](../extensibility/vsix-extension-schema-2-0-reference.md).

 Para abrir o **VSIX Manifest Designer,** localize um arquivo *source.extension.vsixmanifest* no **Solution Explorer**e abra o arquivo. Se o arquivo não contiver XML válido, o designer manifesto não abrirá.

> [!NOTE]
> O arquivo *source.extension.vsixmanifest* é output to *extension.vsixmanifest* quando o pacote é construído.

## <a name="uielement-list"></a>Lista de elementos de interface do usuário
 O **VSIX Manifest Designer** contém quatro seções que correspondem a esses elementos de nível superior do esquema:

- Metadados

- Instalar alvos

- Ativos

- Dependências

  A área de título contém os seguintes controles.

  **Nome do produto** Descreve o nome da extensão.

  **ID do produto** Especifica as informações de identificação exclusivas para este pacote.

  **Autor** Especifica o nome do autor da extensão.

  **Versão** Especifica o número da versão da extensão.

  A guia **Metadados** contém os seguintes controles.

  **Descrição** Fornece uma descrição de texto da extensão, a ser exibida no **Extension Manager**.

  **Língua** Especifica o idioma padrão do pacote, que corresponde aos dados texulos no manifesto. O `Language` atributo segue a convenção de código local de tempo de execução de linguagem comum (CLR) para assembléias de recursos, por exemplo, en-us, en, fr-fr. Por padrão, o valor é neutro, o que significa que o pacote será executado em qualquer versão em idioma do Visual Studio.

  **Licença** Especifica o arquivo de texto que contém a licença do usuário, se houver presente.

  **Ícone** Especifica o arquivo gráfico *(.png*, *.bmp*, *.jpeg*, *.ico*) que contém o ícone a ser exibido no **Gerenciador de extensão**, se um ícone estiver presente. A imagem do ícone deve ser de 32x32 pixels ou é redimensionada para essas dimensões. Se nenhum ícone for especificado, **o Extension Manager** usará um ícone padrão.

  **Visualizar imagem** Especifica o arquivo gráfico *(.png*, *.bmp*, *.jpeg*, *.ico*) que contém a imagem de visualização a ser exibida no **Gerenciador de extensão**, se uma imagem de visualização estiver presente. A imagem de visualização deve ser de 200x200 pixels. Se nenhuma imagem de visualização for especificada, **o Extension Manager** usará uma imagem padrão.

  **Tags** Adiciona tags de texto a serem usadas para dicas de pesquisa.

  **Notas de versão** Especifica um arquivo *(.txt*, *.rtf*) que contém notas de versão. Também pega a URL de um site que exibe as notas de versão.

  **Guia de início** Especifica um arquivo *(.txt*, *.rtf*) que contém informações sobre como usar a extensão ou o conteúdo no pacote VSIX. Este guia aparece quando a instalação da extensão estiver concluída. Também pega a URL de um site que exibe o guia.

  **Mais informações de URL** Especifica a URL de um site que contém informações adicionais sobre o produto.

  A **guia ''''''''''Metas de instalação'.**

  **Tipo de instalação** Lista **o Visual Studio Extension** and Extension **SDK** como tipos de instalação de destino. As opções diferem, dependendo do tipo escolhido.

  **Extensão visual do estúdio** Lista os elementos **InstallationTarget** que descrevem como o pacote pode ser instalado e em quais produtos do Visual Studio essa extensão pode ser instalada. Cada produto é identificado separadamente por nome e uma faixa de versão ou versão. Os produtos podem ser adicionados à lista, modificados e excluídos. O nome e a versão de um produto correspondem aos atributos **Id** e **Version** do elemento **InstallationTarget** associado.

  **O intervalo de** versão é [12.0, 14.0] e usa a seguinte notação:

- [ - versão mínima inclusiva

- ] - versão máxima inclusiva

- ( - versão mínima exclusiva

- - versão máxima exclusiva

- Versão única # - apenas a versão especificada

  **Extensão SDK** Especifica uma instalação global que não esteja escopo de um produto e versão específicos. **O Identificador de Plataforma Alvo** é a plataforma, como o "Windows", que você está mirando. **Target Platform Version** é a versão, como 8.0, da sua plataforma de destino. **SDK Name** e **SDK Versão** são o nome e o número da versão do SDK, respectivamente.

  **Este VSIX é instalado para todos os usuários (requer elevação na instalação)** Se você selecionar esta caixa de seleção, a extensão será instalada para todos os usuários; caso contrário, ele é instalado apenas para o usuário atual.

  **Este VSIX é instalado pelo Windows Installer** Se você selecionar esta caixa de seleção, a extensão será instalada pelo Windows Installer ( arquivo *.msi);* caso contrário, ele é instalado como um pacote VSIX típico *(arquivo .vsix).*

  A guia **Ativos** contém os seguintes controles.

  **Lista de ativos** Lista os elementos de ativo que descrevem a extensão ou os elementos de conteúdo que este pacote aparece. Cada extensão ou elemento de conteúdo é listado separadamente por fonte, tipo e caminho. Extensões e elementos de conteúdo podem ser adicionados à lista, modificados e excluídos. O tipo e o caminho de uma `Type` extensão ou elemento de conteúdo corresponde aos e `Path` atributos do elemento associado. `Asset` Os seguintes tipos são conhecidos:

- Microsoft.VisualStudio.Package

- Microsoft.VisualStudio.MefComponent

- Microsoft.VisualStudio.ToolboxControl

- Microsoft.VisualStudio.Samples

- Modelo microsoft.visualstudio.project

- Modelo microsoft.visualstudio.item

- Microsoft.VisualStudio.Assembly

- Microsoft.ExtensionSDK

  Para adicionar ou editar um ativo, você deve especificar o tipo de ativo, se o ativo é um projeto na solução atual ou um arquivo no sistema de arquivos, e o nome do projeto. Você também pode especificar o nome da pasta em que será incorporada.

  Você também pode criar seus próprios tipos e dar-lhes nomes únicos.

  A guia **Dependências** contém os seguintes controles.

  **Nome, Origem e Faixa de Versão** Lista os elementos de dependência deste pacote, que são outros pacotes dos quais esse pacote depende. Se um pacote de dependência for especificado, ele deve ser instalado antes que este pacote seja instalado; caso contrário, este pacote deve instalá-lo.

  Os pacotes de dependência são especificados por identificador, nome, faixa de versão, origem e como a dependência deve ser resolvida. Cada pacote de dependência é listado separadamente por nome, versão e origem. Os pacotes de dependência podem ser adicionados à lista, modificados e excluídos.

  O identificador deve `ID` corresponder ao atributo dos metadados do pacote de dependência. A fonte pode ser um projeto na solução atual, uma extensão instalada atualmente ou um arquivo. A configuração como é a configuração **de dependência resolvida** pode ser o caminho relativo de um pacote aninhado ou a URL do local de download para a dependência. O ID, a versão e a resolução do `Id`pacote `Version`de `Location` dependência correspondem `Dependency` aos atributos e atributos do elemento associado.

## <a name="see-also"></a>Confira também
- [Referência do esquema de extensão VSIX 2.0](../extensibility/vsix-extension-schema-2-0-reference.md)
- [Anatomia de um pacote VSIX](../extensibility/anatomy-of-a-vsix-package.md)
