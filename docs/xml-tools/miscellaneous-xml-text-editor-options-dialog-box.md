---
title: Caixa de diálogo Diversos, XML, Editor de Texto, Opções
ms.date: 11/04/2016
ms.topic: reference
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 9111613222d25a89b3db55a9d1f3aea39be1f6d8
ms.sourcegitcommit: 21d667104199c2493accec20c2388cf674b195c3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2019
ms.locfileid: "55951677"
---
# <a name="miscellaneous-xml-text-editor-options-dialog-box"></a>Diversos, XML, Editor de texto, caixa de diálogo Opções

Esta caixa de diálogo permite que você altere a automático e as configurações de esquema para o editor XML. Você pode acessar o **opções** caixa de diálogo do **ferramentas** menu.

> [!NOTE]
> Essas configurações estão disponíveis quando você seleciona os **Editor de texto** pasta, o **XML** pasta e, em seguida, o **diversos** opção o **opções** caixa de diálogo.


## <a name="auto-insert"></a>Inserção automática
 **Marcas de fechamento**

 Se a configuração de autocompletar é verificada, o editor adiciona automaticamente uma marca de fim quando você digita um sinal de maior (>) para fechar uma tag de início, se a marca não é fechada. Este é o comportamento padrão.

 A conclusão de um elemento vazio não depende da configuração de autocompletar. Você sempre pode autocomplete um elemento vazio digitando uma barra invertida (/).

 **Aspas de atributo**

 Ao criar atributos XML, o editor insere o caracteres de `=" "` e posiciona o acento circunflexo (^) dentro de aspas duplas.

 Selecionado por padrão.

 **Declarações de namespace**

 O editor inserir automaticamente declarações namespace onde quer que são necessárias.

 Selecionado por padrão.

 **Outra marcação (Comentários, CDATA)**

 Comentários, CDATA, DOCTYPE, as instruções de processamento, e a outra marcação automática são concluídos.

 Selecionado por padrão.

## <a name="network"></a>Rede
 **Baixar automaticamente DTDs e esquemas**

 Os esquemas e as definições de tipo (DTDs) de documentos são baixados automaticamente locais HTTP. Este recurso usa System.Net com a detecção automática do servidor de proxy ativada.

 Selecionado por padrão.

## <a name="outlining"></a>Estrutura de tópicos
 **Entrar no modo de estrutura de tópicos na abertura dos arquivos**

 Ativa o recurso de estruturação quando um arquivo é aberto.

 Selecionado por padrão.

## <a name="caching"></a>Cache
 **Esquemas**

 Especifica o local do cache de esquema. O botão Procurar (**...** ) abre o **Procurar diretório** caixa de diálogo no local de cache de esquema atual. Você pode selecionar um diretório diferente, ou você pode selecionar uma pasta na caixa de diálogo, clique com botão direito e escolha **abrir** para ver o que está no diretório.

## <a name="see-also"></a>Consulte também

- [Propriedades de documento XML, janela Propriedades](../xml-tools/xml-document-properties-properties-window.md)
- [Componentes do editor de XML](../xml-tools/xml-editor-components.md)