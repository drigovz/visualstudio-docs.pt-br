---
title: Propriedades de documento XML, a janela de propriedades
ms.date: 03/05/2019
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 679ac529708a49d18025672ce8f880c4f7710471
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62808126"
---
# <a name="xml-document-properties-properties-window"></a>Propriedades de documento XML, janela Propriedades

O **propriedades** janela fornece informações básicas sobre o documento que está ativo no editor de XML. As propriedades que estão disponíveis varia dependendo do tipo de documento XML que está atualmente ativa.

> [!NOTE]
> Todas as propriedades de documento XML são salvas na solução. Como resultado, você não tem que digitar novamente esses valores na próxima vez que você abrir a solução.

**Encoding**

A codificação de caractere para o arquivo. Alterar essa propriedade também altera o atributo de codificação na declaração XML, e vice-versa. A nova codificação é usado para codificar o arquivo quando você salva o arquivo.

**Entrada**

O documento de entrada associado com a folha de estilos XSLT. Ele é usado pelas **iniciar XSLT** comandos, por exemplo, **XML** > **iniciar sem depuração XSLT**. Um documento pode ser selecionado usando o botão Procurar (**...** ) botão.

Essa propriedade só é visível quando um arquivo XSLT é aberto no editor.

**Saída**

O arquivo que é gerado para transformar um documento XML.

Se um arquivo não for especificado, um nome de arquivo padrão é gerado com base nas `method` atributo a `xsl:output` elemento, que determina a extensão de arquivo. O arquivo padrão é localizado no diretório temporário do usuário atual.

**Esquemas**

Os esquemas a ser usado para validação. O botão abre a **esquemas XSD** caixa de diálogo que pode ser usada para selecionar os esquemas para usar.

Você também pode ir para o caminho para esquemas. Se vários esquemas são especificados, cada caminho de esquema deve ser colocado entre aspas duplas.

**Folha de estilos**

O arquivo XSLT que é usado para transformar o documento quando o **iniciar depuração de XSLT** e **iniciar sem depuração XSLT** comandos são usados. Se esse campo estiver em branco, o editor usa o valor fornecido no `xml-stylesheet` o documento ou instrução de processamento solicitará um nome de arquivo.

Ao editar um arquivo XSLT, essa propriedade pode ser usada para especificar que uma folha de estilo diferente deve ser usado quando o **iniciar depuração de XSLT** ou **iniciar sem depuração XSLT** comando está selecionado. Por exemplo, você talvez queira fazer isso quando você estiver editando uma folha de estilos que está incluída em uma folha de estilos pai.

## <a name="see-also"></a>Consulte também

- [Editor de XML](../xml-tools/xml-editor.md)