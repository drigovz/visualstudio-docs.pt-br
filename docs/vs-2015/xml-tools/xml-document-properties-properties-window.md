---
title: Propriedades do documento XML, janela Propriedades | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: f620cc2bd189dccf067c6276f760d21cde5cf05e
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669514"
---
# <a name="xml-document-properties-properties-window"></a>Propriedades de documento XML, a janela de propriedades
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A janela **Propriedades** fornece informações básicas sobre o documento que está ativo no editor de XML. As propriedades que estão disponíveis varia dependendo do tipo de documento XML que está atualmente ativa.

> [!NOTE]
> Todas as propriedades de documento XML são salvas na solução. Como resultado, você não tem que digitar novamente esses valores na próxima vez que você abrir a solução.

 **Codificação** A codificação de caracteres para o arquivo. Alterar essa propriedade também altera o atributo de codificação na declaração XML, e vice-versa. A nova codificação será usada para codificar o arquivo quando você salvar o arquivo.

 **Entrada** do O documento de entrada associado à folha de estilos XSLT. Ele é usado pelo comando de **saída do exxslt** . Um documento pode ser selecionado usando o botão procurar ( **...** ).

 Esta propriedade é visível somente quando um arquivo fonte é atualmente ativa na janela editor.

 **Saída** do O arquivo que é gerado ao transformar um documento XML.

 Se um arquivo é não especificado, um nome de arquivo padrão é gerado com base no atributo de `method` no elemento de `xsl:output` que determina a extensão de arquivo. O arquivo padrão é localizado no diretório temporário do usuário atual.

 **Esquemas** Os esquemas a serem usados para validação. O botão abre a caixa de diálogo **esquemas XSD** , que pode ser usada para selecionar os esquemas a serem usados.

 Você também pode ir para o caminho para esquemas. Se vários esquemas são especificados, cada caminho de esquema deve ser colocado entre aspas duplas.

 **Folha de estilos** O arquivo XSLT que é usado para transformar o documento quando o comando **Mostrar saída XSLT** é usado. Se esse campo estiver em branco quando o comando **Mostrar saída XSLT** for usado, o editor usará o valor fornecido na `xml-stylesheet` instrução de processamento do documento ou solicitará o nome do arquivo.

 Ao editar um arquivo XSLT, essa propriedade pode ser usada para especificar que uma folha de estilos diferente deve ser usada quando o comando Mostrar XSLT de **saída** ou de **depuração** está selecionado. Por exemplo, você pode querer fazer isso quando você estiver editando uma folha de estilos incluída em uma folha de estilos pai.

## <a name="see-also"></a>Consulte também
 [Componentes do editor XML](../xml-tools/xml-editor-components.md) do [editor XML](../xml-tools/xml-editor.md)
