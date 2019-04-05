---
title: Diversos, XML, Editor de texto, opções de caixa de diálogo | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: fd3fff31-cddc-422d-a2f0-a5a1ef492afd
caps.latest.revision: 9
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 0181609f083aada564edb585f64ccdaaf104ed15
ms.sourcegitcommit: 8b538eea125241e9d6d8b7297b72a66faa9a4a47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "58922591"
---
# <a name="miscellaneous-xml-text-editor-options-dialog-box"></a>Caixa de diálogo Diversos, XML, Editor de Texto, Opções
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

  
Esta caixa de diálogo permite que você altere a automático e as configurações de esquema para o editor XML. Você pode acessar o **opções** caixa de diálogo do **ferramentas** menu.  
  
> [!NOTE]
>  Essas configurações estão disponíveis quando você seleciona os **Editor de texto** pasta, o **XML** pasta e, em seguida, o **diversos** opção o **opções** caixa de diálogo.  
  
## <a name="auto-insert"></a>AutoInserção  
 **Marcas de fechamento**  
 Se a configuração de AutoCompletar é verificada, o editor adiciona automaticamente uma marca de fim quando você digita um colchete angular direito (>) para fechar uma tag de início, se a marca não já está fechada. Este é o comportamento padrão.  
  
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
 [Propriedades de documento XML, janela Propriedades](../xml-tools/xml-document-properties-properties-window.md)   
 [Componentes do editor de XML](../xml-tools/xml-editor-components.md)
