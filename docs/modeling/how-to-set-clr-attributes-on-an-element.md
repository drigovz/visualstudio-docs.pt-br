---
title: Como definir atributos CLR em um elemento
ms.date: 11/04/2016
ms.topic: conceptual
f1_keywords:
- vs.dsltools.EditAttributesDialog
helpviewer_keywords:
- Domain-Specific Language, custom attrributes
author: jillre
ms.author: jillfra
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f943f9713e4432f0b06242a2f66acae6b390e5cc
ms.sourcegitcommit: 5f6ad1cefbcd3d531ce587ad30e684684f4c4d44
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/22/2019
ms.locfileid: "72748361"
---
# <a name="how-to-set-clr-attributes-on-an-element"></a>Como definir atributos CLR em um elemento
Atributos personalizados são atributos especiais que podem ser adicionados a elementos de domínio, formas, conectores e diagramas. Você pode adicionar qualquer atributo que herda da classe `System.Attribute`.

### <a name="to-add-a-custom-attribute"></a>Para adicionar um atributo personalizado

1. No **Gerenciador de DSL**, selecione o elemento ao qual você deseja adicionar um atributo personalizado.

2. Na janela **Propriedades** , ao lado da propriedade **atributos personalizados** , clique no ícone procurar ( **...** ).

     A caixa de diálogo **Editar atributos** é aberta.

3. Na coluna **nome** , clique em **\<add atributo >** e digite o nome do seu atributo. Pressione ENTER.

4. A linha abaixo do nome do atributo mostra parênteses. Nessa linha, digite um tipo de parâmetro para o atributo (por exemplo, `string`) e pressione ENTER.

5. Na coluna **propriedade de nome** , digite um nome apropriado, por exemplo, `MyString`.

6. Clique em **OK**.

     A propriedade **atributos personalizados** agora exibe o atributo no seguinte formato:

     `[` *AttributeName* `(` *tipo* de `=` do *ParameterName* `)]`

## <a name="see-also"></a>Consulte também

- [Glossário das Ferramentas de Linguagem Específica de Domínio](https://msdn.microsoft.com/ca5e84cb-a315-465c-be24-76aa3df276aa)