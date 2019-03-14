---
title: Opções, Editor de texto, XML, Diversos
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: d3421580251a6a871adba311fd609e881e088ebd
ms.sourcegitcommit: 3ca33862c1cfc3ccb83de3e95f1e69e860ab143a
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57525076"
---
# <a name="options-text-editor-xml-miscellaneous"></a>Opções, Editor de texto, XML, Diversos

Use a página de opções **Diversos** para alterar as configurações de preenchimento automático e de esquema para o Editor XML. Para acessar as opções de XML diversas, escolha **Ferramentas** > **Opções** > **Editor de texto** > **XML** e, em seguida, escolha **Diversos**.

## <a name="auto-insert"></a>AutoInserção

**Marcas de fechamento**

O editor de texto adiciona marcas de fechamento ao criar elementos XML. Se uma marca de início de elemento for selecionada, o editor inserirá a marca de fechamento correspondente, incluindo um prefixo de namespace correspondente. Por padrão, a caixa de seleção fica marcada.

**Aspas de atributo**

Ao criar atributos XML, o editor insere os caracteres `="` e `"` e posiciona o acento circunflexo (**^**) dentro de aspas duplas. Por padrão, a caixa de seleção fica marcada.

**Declarações de namespace**

O editor inserir automaticamente declarações namespace onde quer que são necessárias. Por padrão, a caixa de seleção fica marcada.

**Outra marcação (Comentários, CDATA)**

Comentários, CDATA, DOCTYPE, instruções de processamento e a outra marcação automática são concluídos. Por padrão, a caixa de seleção fica marcada.

## <a name="network"></a>Rede

**Baixar automaticamente DTDs e esquemas**

Os esquemas e as definições de tipo (DTDs) de documentos são baixados automaticamente locais HTTP. Esse recurso usa o System.Net com a detecção do servidor autoproxy habilitada. Por padrão, a caixa de seleção fica marcada.

## <a name="outlining"></a>Estrutura de tópicos

**Entrar no modo de estrutura de tópicos na abertura dos arquivos**

Ativa o recurso de estruturação quando um arquivo é aberto. Por padrão, a caixa de seleção fica marcada.

## <a name="caching"></a>Cache

**Esquemas**

Especifica o local do cache de esquema. O botão **Procurar** abre a localização do cache do esquema atual em uma nova janela. O local padrão é *%VsInstallDir%\xml\Schemas*.

## <a name="see-also"></a>Consulte também

- [Opções de XML – Formatação](options-text-editor-xml-formatting.md)
- [Ferramentas XML no Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)