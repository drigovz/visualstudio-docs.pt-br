---
title: Tabela de Comando do Visual Studio (. Vsct) Arquivos | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: d18367436d1ee1b889558a35723e4e3cec865945
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704033"
---
# <a name="visual-studio-command-table-vsct-files"></a>Arquivos .Vsct (Visual Studio Command Table)
Um arquivo de configuração da tabela de comando é um arquivo de texto que descreve o conjunto de comandos que um VSPackage contém. O [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] compilador da tabela de comando (VSCT) compila arquivos de configuração baseados em XML (arquivos.vsct) em arquivos de saída de tabela de comando binário (.cto). Os arquivos .cto resultantes são os mesmos que são criados usando o compilador da tabela de comando (CTC) para compilar arquivos de configuração .ctc. No entanto, os arquivos .vsct baseados em XML têm algumas vantagens, como um editor XML e o XML IntelliSense.

 Para saber mais sobre a sintaxe e semântica dos arquivos .vsct, consulte [Designing XML Command Table (. Vsct) Arquivos](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

## <a name="in-this-section"></a>Nesta seção
 [Projetar arquivos da tabela de comandos XML (.Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)

 Descreve como projetar arquivos .vsct.

 [Como criar um arquivo .Vsct](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)

 Compara os métodos para criar um arquivo .vsct. Descreve o processo para criar manualmente um novo arquivo .vsct.

## <a name="related-sections"></a>Seções relacionadas
 [Referência do esquema XML do VSCT](../../extensibility/vsct-xml-schema-reference.md)

 Fornece detalhes sobre cada seção do arquivo de configuração XML da tabela de comando.

 [Configuração da tabela de comando (. Ctc) Arquivos](https://msdn.microsoft.com/library/3413dda1-f372-4669-bcf0-c64d3463842c) Apresenta uma visão geral do formato de arquivo .ctc depreciado.

 [Como os VSPackages adicionam elementos da interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)

 Descreve a especificação do formato da tabela de comando.

 [Recursos em VSPackages](../../extensibility/internals/resources-in-vspackages.md)

 Descreve como usar recursos gerenciados e não gerenciados em VSPackages gerenciados.

 [Comandos, menus e barras de ferramentas](../../extensibility/internals/commands-menus-and-toolbars.md)

 Explica como criar uma ia que inclua menus, barras de ferramentas e caixas de comando.
