---
title: Opções, Editor de Texto, Extensão de Arquivo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: reference
f1_keywords:
- vs.toolsoptionspages.text_editor.file_extension
helpviewer_keywords:
- file extensions, associating to editor
- Editing Experience
- Options dialog box
- Editing Experience, selecting
ms.assetid: 05298fc5-fc4e-4bb2-b942-1f7d2dcdff0f
caps.latest.revision: 16
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 26c53633bc55efcf95ffbc579e24d2d61e4a0932
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72662271"
---
# <a name="options-text-editor-file-extension"></a>Opções, Editor de Texto, Extensão de Arquivo
[!INCLUDE[vs2017banner](../../includes/vs2017banner.md)]

A caixa de diálogo Opções permite especificar como todos os arquivos com determinadas extensões de arquivo serão manipulados pelo IDE (ambiente de desenvolvimento integrado) do Visual Studio. Para cada **Extensão** que inserir, você pode selecionar uma Experiência de Edição. Isso permite escolher o editor ou o designer do IDE no qual os documentos de um determinado tipo serão abertos. Para exibir essas opções, escolha **Opções** no menu **Ferramentas**, expanda o nó **Editor de Texto** e selecione **Extensão de Arquivo**.

 Quando você selecionar uma opção "com codificação", uma caixa de diálogo será exibida sempre que você abrir um documento do tipo em questão que permitir selecionar um esquema de codificação para o documento. Isso pode ser útil se você estiver preparando versões dos documentos do projeto para uso em diferentes plataformas ou em diferentes linguagens de destino.

> [!NOTE]
> As caixas de diálogo e os comandos de menu encontrados podem diferir daqueles descritos na Ajuda, dependendo das configurações ativas ou edição. Para alterar suas configurações, selecione **Importar e Exportar Configurações** no menu **Ferramentas** . Para obter mais informações, consulte [Personalizando configurações de desenvolvimento no Visual Studio](https://msdn.microsoft.com/22c4debb-4e31-47a8-8f19-16f328d7dcd3).

## <a name="uielement-list"></a>Lista de elementos de interface do usuário
 **Extensão** do Digite a extensão de arquivo cuja experiência de edição no IDE você deseja definir.

 **Editor** do Selecione o editor de IDE ou o designer no qual os documentos com essa extensão de arquivo serão abertos. Quando você selecionar uma opção "com codificação", uma caixa de diálogo será exibida sempre que você abrir um documento do tipo em questão que permitir selecionar um esquema de codificação.

 **Adicionar** Adiciona uma entrada que inclui **Extensão** e **Experiência de Edição** especificados à Lista de Extensão.

 **Remover** Exclui a entrada selecionada da lista de extensões.

 Lista de extensões lista todas as extensões para as quais uma experiência de edição foi especificada.

 **Mapear arquivos com extensão para** Selecione esta opção se desejar especificar como os arquivos sem uma extensão serão manipulados pelo IDE.

 **Opções de arquivo com extensão** Fornece a mesma lista que o **Editor**. Selecione o editor ou o designer do IDE em que documentos sem extensão de arquivo serão abertos.

## <a name="see-also"></a>Consulte Também
 [Como gerenciar modos do editor](../../ide/how-to-manage-editor-modes.md)
