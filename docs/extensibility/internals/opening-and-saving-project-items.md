---
title: Abertura e Economia de Itens do Projeto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- projects [Visual Studio SDK], file persistence
- files [Visual Studio], opening and saving
- editors [Visual Studio SDK], file persistence
ms.assetid: f71898ad-335f-4c43-a177-4da87078afd1
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: bbb89d99e401be6bae7d8ee9be8ee33fa7574723
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80706963"
---
# <a name="opening-and-saving-project-items"></a>Abrindo e salvando itens de projeto
Quando você adiciona um novo tipo de projeto, você deve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] gerenciar a abertura e a salvação de seus arquivos de projetos no ambiente de desenvolvimento integrado (IDE). Os tópicos a seguir discutem as diferentes abordagens para abrir e salvar arquivos.

## <a name="in-this-section"></a>Nesta seção
- [Exibindo arquivos usando o comando Abrir Arquivo](../../extensibility/internals/displaying-files-by-using-the-open-file-command.md)

 Fornece uma explicação passo-a-passo de como o IDE lida com o comando **Arquivo Aberto** e o papel dos projetos na resposta a este comando.

- [Exibindo arquivos usando o comando Abrir Com](../../extensibility/internals/displaying-files-by-using-the-open-with-command.md)

 Fornece uma explicação detalhada e passo a passo de como o IDE lida com o comando **Open With,** solicitando a abertura de um arquivo que tenha alguma escolha de editores padrão.

- [Como abrir editores específicos a um projeto](../../extensibility/how-to-open-project-specific-editors.md)

 Fornece instruções passo-a-passo para especificar que arquivos de um determinado tipo em seu projeto devem ser abertos usando um editor específico do projeto.

- [Como abrir editores padrão](../../extensibility/how-to-open-standard-editors.md)

 Fornece instruções passo-a-passo para especificar como habilitar o IDE para abrir um editor padrão para arquivos do seu tipo de projeto.

- [Como abrir editores para documentos abertos](../../extensibility/how-to-open-editors-for-open-documents.md)

 Fornece instruções passo a passo para abrir um editor específico do projeto para um arquivo aberto.

- [Salvando um documento padrão](../../extensibility/internals/saving-a-standard-document.md)

 Fornece uma explicação detalhada de como o IDE lida com os comandos **Save,** **Save As**e **Save All** para um documento aberto em um editor padrão.

- [Salvando um documento personalizado](../../extensibility/internals/saving-a-custom-document.md)

 Fornece um diagrama e uma explicação detalhada de como o IDE lida com os comandos **Save,** **Save As**e Save **All para** documentos abertos em um editor personalizado.

- [Determinando qual editor abre um arquivo em um projeto](../../extensibility/internals/determining-which-editor-opens-a-file-in-a-project.md)

 Discute o processo que o IDE segue para selecionar o editor ou designer apropriado para um arquivo.

## <a name="related-sections"></a>Seções relacionadas
- [Criar designers e editores personalizados](../../extensibility/creating-custom-editors-and-designers.md)

 Lista os quatro tipos de editores que o IDE pode hospedar e dá descrições de cada editor.

- [Tipos de projeto](../../extensibility/internals/project-types.md)

 Discute como os projetos controlam a forma como esse código é compilado e construído, como os editores são abertos e como os itens do projeto são formatados.
