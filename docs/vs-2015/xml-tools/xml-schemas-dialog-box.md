---
title: Caixa de diálogo esquemas XML | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: 0271fa26-2205-49bd-96e0-ae1441571808
caps.latest.revision: 9
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: d637cb3c25772685d5a782eb74bf94878ded36c2
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669429"
---
# <a name="xml-schemas-dialog-box"></a>A caixa de diálogo de esquemas XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

A caixa de diálogo **esquemas XML** é usada para selecionar quais esquemas XSD (linguagem de definição de esquema XML) associar a um documento XML. Você pode selecionar um esquema de cache do esquema, ou especificar um esquema que não está localizado no cache. Os esquemas selecionados são considerados parte de um conjunto de esquema. O esquema é usado para o IntelliSense e também validação de documento XML.

 Você pode acessar a caixa de diálogo **esquemas XML** clicando no botão **esquemas** na janela Propriedades do documento ou selecionando **esquemas** no menu **XML** .

## <a name="uielement-list"></a>Lista UIElement
 **Usar** o Selecione como o esquema XML deve ser usado.

- **Automático**. Este esquema não está em uso pelo documento atual mas está disponível para a associação automática. Se o documento XML declarar um namespace que corresponde `targetNamespace` deste esquema, o esquema será associado e é automaticamente encapsulado no conjunto de esquema.

- **Use este esquema**. Este esquema está sendo usado pelo documento atual. Qualquer o usuário que solicitou explicitamente este esquema está usado clicando nessa coluna, ou o esquema foi associado automaticamente com base em `targetNamespace`correspondente.

- Não **use esquemas selecionados**. Este esquema não é usado pelo documento atual, mesmo se o esquema tem `targetNamespace`correspondente. Essa configuração pode ser útil para resolver conflitos quando há mais de uma versão do mesmo esquema no cache ou na solução de esquema.

  **Namespace de destino** Exibe o namespace de destino associado ao esquema XML.

  **Nome do arquivo** Exibe o nome do arquivo de esquema XML.

  **Adicionar** Abre a caixa de diálogo **abrir esquema XSD** , que permite que você selecione esquemas adicionais para adicionar ao conjunto de esquema. Quando você adiciona um esquema ao conjunto de esquema, o valor de coluna de **uso** é definido para **usar esse esquema**.

  **Remover** Remove o esquema atualmente selecionado do conjunto de esquema. Remove o esquema de cache de memória do esquema, mas não no sistema de arquivos.

## <a name="see-also"></a>Consulte também
 [Componentes do editor de XML](../xml-tools/xml-editor-components.md) [como: selecionar os esquemas XML para usar o cache de](../xml-tools/how-to-select-the-xml-schemas-to-use.md) [esquema](../xml-tools/schema-cache.md)
