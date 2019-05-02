---
title: Validação de documento XML no editor de XML
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: abb353bd-6c4a-4978-b03b-a8c245bbfb55
author: gewarren
ms.author: gewarren
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: 59b8ed5c74d998b47ff4a187b420695eab5be035
ms.sourcegitcommit: 94b3a052fb1229c7e7f8804b09c1d403385c7630
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62807707"
---
# <a name="xml-document-validation"></a>Validação de documento XML

O editor de XML verifica a sintaxe XML 1.0 e também realiza validação de dados conforme você digita. O editor pode validar usando uma DTD (definição de tipo de documento) ou um esquema. Os sublinhados ondulados vermelhos realçam todos os erros de XML 1.0 bem-formado. Os sublinhados ondulados azuis mostram os erros semânticos com base na validação de DTD ou de esquema. Cada erro tem uma entrada associada na lista de erros. Você também pode exibir a mensagem de erro pausando o mouse sobre o sublinhado ondulado.

 Os esquemas usados na validação são encontrados correspondendo o `targetNamespace` de um esquema compilado com a declaração xmlns do elemento. Os esquemas compilados são carregados de um dos seguintes locais, listados por ordem de prioridade:

- Do nome de arquivo especificado na **esquemas** campo do documento **propriedades** janela.

- Um esquema ou DTD embutido.

- Uma DTD externa ou os atributos `xsd:schemaLocation` e `xsd:noNamespaceSchemaLocation`

- Um URI de um namespace do esquema XDR "x-schema".

Os esquemas também podem ser encontrados nos seguintes locais adicionais quando o esquema tiver um namespace de destino não vazio:

- Outra janela do editor que contenha o esquema.

- Um esquema na solução atual.

- Um esquema do diretório de cache de esquema.

## <a name="xslt-files"></a>Arquivos XSLT
 Ao editar um arquivo XSLT, o *XSLT* arquivo localizado no cache do esquema é usado para validação. Os erros de validação são mostrados como sublinhados ondulados azuis. Os erros do compilador XSLT são mostrados como sublinhados ondulados vermelhos.

## <a name="xml-schema-xsd-files"></a>Arquivos de esquema (XSD) de XML
 Ao editar um arquivo de esquema XML, o *xsdschema* arquivo localizado no cache do esquema é usado para validação. Os erros de validação são mostrados como sublinhados ondulados azuis. Todos os erros de compilação também são mostrados com traços ondulados vermelhos.

## <a name="see-also"></a>Consulte também

- [Editor de XML](../xml-tools/xml-editor.md)