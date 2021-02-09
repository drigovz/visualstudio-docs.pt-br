---
title: Propriedades de documento XML, a janela de propriedades
description: Saiba mais sobre as propriedades de documento XML no janela Propriedades que fornecem informações básicas sobre o documento ativo no editor de XML.
ms.custom: SEO-VS-2020
ms.date: 03/05/2019
ms.topic: reference
ms.assetid: 9dbb34d9-02ea-4201-b445-c98a0eb0d6db
author: TerryGLee
ms.author: tglee
manager: jmartens
ms.workload:
- multiple
ms.openlocfilehash: 1e12118f2f7f5d9189ca768f7be65a35b490eb54
ms.sourcegitcommit: ae6d47b09a439cd0e13180f5e89510e3e347fd47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/08/2021
ms.locfileid: "99875010"
---
# <a name="xml-document-properties-properties-window"></a>Propriedades de documento XML, janela Propriedades

A janela **Propriedades** fornece informações básicas sobre o documento que está ativo no editor de XML. As propriedades que estão disponíveis varia dependendo do tipo de documento XML que está atualmente ativa.

> [!NOTE]
> Todas as propriedades de documento XML são salvas na solução. Como resultado, você não tem que digitar novamente esses valores na próxima vez que você abrir a solução.

**Codificação**

A codificação de caractere para o arquivo. Alterar essa propriedade também altera o atributo de codificação na declaração XML, e vice-versa. A nova codificação é usada para codificar o arquivo quando você salva o arquivo.

**Entrada**

O documento de entrada associado com a folha de estilos XSLT. Ele é usado pelos comandos **Start XSLT** , por exemplo, **XML**  >  **Start XSLT sem depuração**. Um documento pode ser selecionado usando o botão procurar (**...**).

Essa propriedade só é visível quando um arquivo XSLT é aberto no editor.

**Saída**

O arquivo que é gerado para transformar um documento XML.

Se um arquivo não for especificado, um nome de arquivo padrão será gerado com base no `method` atributo no `xsl:output` elemento, que determina a extensão do arquivo. O arquivo padrão é localizado no diretório temporário do usuário atual.

**Esquemas**

Os esquemas a ser usado para validação. O botão abre a caixa de diálogo **esquemas XSD** , que pode ser usada para selecionar os esquemas a serem usados.

Você também pode ir para o caminho para esquemas. Se vários esquemas são especificados, cada caminho de esquema deve ser colocado entre aspas duplas.

**Xls**

O arquivo XSLT usado para transformar o documento quando os comandos **Iniciar Depuração XSLT** e **Iniciar XSLT sem depuração** são usados. Se esse campo estiver em branco, o editor usará o valor fornecido na `xml-stylesheet` instrução de processamento do documento ou solicitará um nome de arquivo.

Ao editar um arquivo XSLT, essa propriedade pode ser usada para especificar que uma folha de estilos diferente deve ser usada quando o comando **Iniciar Depuração XSLT** ou **Iniciar XSLT sem depuração** está selecionado. Por exemplo, talvez você queira fazer isso quando estiver editando uma folha de estilos que está incluída em uma folha de estilos pai.

## <a name="see-also"></a>Confira também

- [Editor de XML](../xml-tools/xml-editor.md)
