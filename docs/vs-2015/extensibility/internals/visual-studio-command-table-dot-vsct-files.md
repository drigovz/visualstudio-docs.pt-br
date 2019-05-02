---
title: Tabela de comando do Visual Studio (. Arquivos VSCT) | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- VSCT files, overview
- Visual Studio command table configuration files (VSCT), overview
ms.assetid: 1313adb4-add4-4e74-90e2-f4be522f5259
caps.latest.revision: 23
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: 98b3892d10b003d6236ae9ccfbebb83a602a5877
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58922862"
---
# <a name="visual-studio-command-table-vsct-files"></a>Arquivos .Vsct (Visual Studio Command Table)
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

Um arquivo de configuração da tabela de comando é um arquivo de texto que descreve o conjunto de comandos que contém um VSPackage. O [!INCLUDE[vsprvs](../../includes/vsprvs-md.md)] comando compilador tabela (VSCT) compila a configuração baseada em XML (arquivos. VSCT) em arquivos de saída (CTO já) da tabela de comando binário. Os arquivos de CTO já resultantes são iguais aos que são criados usando o compilador de tabela (CTC) do comando para compilar os arquivos de configuração. ctc. No entanto, os arquivos. VSCT de baseado em XML tem algumas vantagens, como um editor de XML e o IntelliSense XML.  
  
 Para saber mais sobre a sintaxe e semântica de arquivos. VSCT, consulte [criar tabela de comando de XML (. Arquivos de VSCT)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
  
## <a name="in-this-section"></a>Nesta seção  
 [Projetar arquivos da tabela de comandos XML (.Vsct)](../../extensibility/internals/designing-xml-command-table-dot-vsct-files.md)  
 Descreve como criar arquivos. VSCT.  
  
 [Como: Criar um. Arquivo VSCT](../../extensibility/internals/how-to-create-a-dot-vsct-file.md)  
 Compara os métodos para a criação de um arquivo. VSCT. Descreve o processo de criação manual de um novo arquivo. VSCT.  
  
## <a name="related-sections"></a>Seções relacionadas  
 [Referência do esquema XML do VSCT](../../extensibility/vsct-xml-schema-reference.md)  
 Fornece detalhes sobre cada seção do arquivo de configuração do XML do comando tabela.  
  
 [Configuração da tabela de comando (. Arquivos CTC)](http://msdn.microsoft.com/3413dda1-f372-4669-bcf0-c64d3463842c)  
 Apresenta uma visão geral do formato de arquivo. ctc preterido.  
  
 [Como os VSPackages adicionam elementos da interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)  
 Descreve a especificação de formato de tabela do comando.  
  
 [Recursos em VSPackages](../../extensibility/internals/resources-in-vspackages.md)  
 Descreve como usar os recursos gerenciados e em VSPackages gerenciados.  
  
 [Comandos, menus e barras de ferramentas](../../extensibility/internals/commands-menus-and-toolbars.md)  
 Explica como criar uma interface do usuário que inclui menus, barras de ferramentas e caixas de combinação de comando.
