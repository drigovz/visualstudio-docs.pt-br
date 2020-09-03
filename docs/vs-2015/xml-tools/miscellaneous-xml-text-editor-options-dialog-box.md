---
title: Miscelânea, XML, editor de texto, caixa de diálogo opções | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d30564c11951d6ffec420c6a2ea95c41695de3dd
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "72656244"
---
# <a name="miscellaneous-xml-text-editor-options-dialog-box"></a>Caixa de diálogo Diversos, XML, Editor de Texto, Opções
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Esta caixa de diálogo permite que você altere a automático e as configurações de esquema para o editor XML. Você pode acessar a caixa de diálogo **Opções** no menu **Ferramentas**.

> [!NOTE]
> Essas configurações estão disponíveis quando você seleciona a pasta **Editor de texto** , a pasta **XML** e a opção **diversos** da caixa de diálogo **Opções** .

## <a name="auto-insert"></a>Inserir automaticamente
 **Marcas de fechamento** Se a configuração de conclusão automática estiver marcada, o editor adicionará automaticamente uma marca de fim quando você digitar um colchete angular direito (>) para fechar uma marca de início, se a marca ainda não estiver fechada. Esse é o comportamento padrão.

 A conclusão de um elemento vazio não depende da configuração de autocompletar. Você sempre pode autocomplete um elemento vazio digitando uma barra invertida (/).

 **Aspas de atributo** Ao criar atributos XML, o editor insere os `=" "` caracteres e posiciona o circunflexo (^) dentro das aspas duplas.

 Selecionadas por padrão.

 **Declarações de namespace** O editor insere automaticamente declarações de namespace onde quer que sejam necessárias.

 Selecionadas por padrão.

 **Outra marcação (comentários, CDATA)** Comentários, CDATA, DOCTYPE, instruções de processamento e outras marcações são concluídas automaticamente.

 Selecionadas por padrão.

## <a name="network"></a>Rede
 **Baixar automaticamente DTDs e esquemas** Esquemas e definições de tipo de documento (DTDs) são baixados automaticamente de locais HTTP. Este recurso usa System.Net com a detecção automática do servidor de proxy ativada.

 Selecionadas por padrão.

## <a name="outlining"></a>Estrutura de tópicos
 **Entrar no modo de estrutura de tópicos quando os arquivos forem abertos** Ativa o recurso de estrutura de tópicos quando um arquivo é aberto.

 Selecionadas por padrão.

## <a name="caching"></a>Cache
 **Esquemas** Especifica o local do cache de esquema. O botão procurar (**...**) abre a caixa de diálogo **pesquisa de diretório** no local do cache de esquema atual. Você pode selecionar um diretório diferente, ou pode selecionar uma pasta na caixa de diálogo, clicar com o botão direito do mouse e escolher **abrir** para ver o que está no diretório.

## <a name="see-also"></a>Consulte Também
 [Propriedades de documento XML, janela Propriedades](../xml-tools/xml-document-properties-properties-window.md) [componentes do editor XML](../xml-tools/xml-editor-components.md)
