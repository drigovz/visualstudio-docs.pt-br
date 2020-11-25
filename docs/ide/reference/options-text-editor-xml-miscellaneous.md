---
title: Opções, Editor de texto, XML, Diversos
description: Saiba como usar a página diversos na seção XAML para alterar as configurações de preenchimento automático e esquema para o editor de XML.
ms.custom: SEO-VS-2020
ms.date: 10/29/2018
ms.topic: reference
f1_keywords:
- VS.ToolsOptionsPages.Text_Editor.XML.Miscellaneous
ms.assetid: b6538cbe-badd-4313-a1fb-39e906736bbe
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.openlocfilehash: a02a2a133031661ecbf9c3719f3b1993f3b20b5b
ms.sourcegitcommit: 967c2f8c1b3f805cf42c0246389517689d971b53
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/25/2020
ms.locfileid: "96040106"
---
# <a name="options-text-editor-xml-miscellaneous"></a>Opções, Editor de texto, XML, Diversos

Use a página de opções **Diversos** para alterar as configurações de preenchimento automático e de esquema para o Editor XML. Para acessar opções de XML diversas, escolha **ferramentas**  >  **Opções**  >  **Editor de texto**  >  **XML** e, em seguida, escolha **diversos**.

## <a name="auto-insert"></a>Inserir automaticamente

**Fechar marcas**

O editor de texto adiciona marcas de fechamento ao criar elementos XML. Se uma marca de início de elemento for selecionada, o editor insere a marca íntima correspondente, incluindo um prefixo de namespace correspondente. Esta caixa de seleção fica marcada por padrão.

**Citações de atributo**

Ao criar atributos XML, o editor insere os `="` caracteres e `"` e posiciona o circunflexo ( **^** ) dentro das aspas. Esta caixa de seleção fica marcada por padrão.

**Declarações de namespace**

O editor insere declarações de namespace automaticamente onde quer elas sejam necessárias. Esta caixa de seleção fica marcada por padrão.

**Outra remarcação (Comentários, CDATA)**

Comentários, CDATA, DOCTYPE, instruções de processamento e outra remarcação e autocompletada. Esta caixa de seleção fica marcada por padrão.

## <a name="network"></a>Rede

**Carregar automaticamente DTDs e esquemas**

Esquemas e DTDs (definições de tipo de documento) são baixados automaticamente de locais HTTP. Esse recurso usa System.Net com detecção de servidor de autoproxy habilitada. Esta caixa de seleção fica marcada por padrão.

## <a name="outlining"></a>Estrutura de tópicos

**Entrar no modo de estrutura de tópicos quando os arquivos forem abertos**

Ativa o recurso de estrutura de tópicos quando um arquivo é aberto. Esta caixa de seleção fica marcada por padrão.

## <a name="caching"></a>Cache

**Esquemas**

Especifica o local do cache de esquema. O botão **Procurar** abre a localização do cache do esquema atual em uma nova janela. O local padrão é *%VsInstallDir%\xml\Schemas*.

## <a name="see-also"></a>Confira também

- [Opções de XML – Formatação](options-text-editor-xml-formatting.md)
- [Ferramentas XML no Visual Studio](../../xml-tools/xml-tools-in-visual-studio.md)
