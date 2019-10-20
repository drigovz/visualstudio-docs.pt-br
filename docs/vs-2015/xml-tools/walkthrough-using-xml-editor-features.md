---
title: 'Walkthrough: usando recursos do editor de XML | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: ea8dc357-2e66-455a-aec2-7ccaccfc9adf
caps.latest.revision: 4
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: fa954cfb356593a4f22a44faddd69acdcfc93e37
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72669561"
---
# <a name="walkthrough-using-xml-editor-features"></a>Passo a passo: Usando recursos do editor XML
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

As etapas nessa explicação passo a passo mostram como criar um novo documento XML. A explicação passo a passo também usa alguns dos recursos do editor XML que tornam valioso para criar XML.

> [!NOTE]
> Antes de iniciar a explicação passo a passo, salve o arquivo de hireDate.xsd (incluído abaixo neste tópico) para seu computador local.

### <a name="to-create-a-new-xml-file-and-associate-it-with-an-xml-schema"></a>Para criar um novo arquivo XML e associá-la com um esquema XML

1. No menu **arquivo** , aponte para **novo**e clique em **arquivo**.

2. Selecione **arquivo XML** no painel **modelos** e clique em **abrir**.

     Um novo arquivo é aberto no editor. O arquivo contém uma declaração XML padrão, `<?xml version="1.0" encoding="utf-8">`.

3. Na janela Propriedades do documento, clique no botão procurar ( **...** ) no campo **esquemas** .

     A caixa de diálogo **esquemas XSD** é exibida.

4. Clique em **Adicionar**.

     A caixa de diálogo **abrir esquema XSD** é exibida.

5. Selecione o arquivo HireDate. xsd e clique em **abrir**.

6. Clique em **OK**.

     O esquema XML agora está associado com o documento XML. O esquema XML é usado para validar o documento. Também é usado pelo IntelliSense para preencher a lista de membros de elementos válidos.

### <a name="to-add-data"></a>Para adicionar dados

1. Tipo `<` no painel do editor.

     A lista de membros exibe os itens possíveis:

    - **!--** adicionar um comentário.

    - **! DOCTYPE** para adicionar um tipo de documento.

    - **?** para adicionar uma instrução de processamento.

    - **funcionário** para adicionar o elemento raiz.

2. Selecione **\<!--** para adicionar um nó de comentário e pressione Enter.

     O editor insere uma marca de fim do comentário e colocar o cursor entre o início e marcas de comentário final.

3. Digite o **arquivo XML de teste**.

4. Em uma nova linha, digite `<` e selecione **funcionário** na lista de membros.

     O editor adiciona o início de um elemento XML, `<employee`. Neste momento você pode adicionar atributos para o elemento ou você pode fechar a tag de início digitando `>`.

5. Tipo `>` para a marca de fechamento.

6. O editor adiciona a marca de fim. A marca de fim é adicionada com um a linha subescrita ondulada que indica um erro de validação. A dica de ferramenta exibe a mensagem: O elemento “empregado” tem conteúdo incompleto. 'ID' esperado.

7. Digite `<` e selecione **ID** na lista de membros. Digite `>`.

     O editor adicione o elemento XML, `<ID></ID>`, e posicionar o cursor após a marca de início de identificação.

8. Digite **ABC**.

     O texto **ABC** tem um sublinhado ondulado. A dica de ferramenta exibe a mensagem: O elemento “identificação” tem um valor inválido de acordo com seu tipo de dados.

9. Clique com o botão direito do mouse no elemento ID e selecione **ir para definição**.

     O editor abre o arquivo de hireDate.xsd em uma nova janela de documento e posicionar o cursor na definição de elemento do esquema de identificação.

10. Retorne ao arquivo XML e substitua o texto **ABC** por **123**.

     O sublinhado e o ToolTip ondulados são desmarcados no valor do elemento ID. A dica de ferramenta para a marca de fim do funcionário agora exibe a mensagem: O elemento “empregado” tem conteúdo incompleto. “Data de admissão esperada”.

11. Coloque o cursor após a marca de fim de identificação, digite `<`, data de admissão select da lista de membros, e digite dentro `>`.

     O editor adicione o elemento XML, `<hire-date></hire-date>`, e posicionar o cursor após a marca de início da data de admissão.

12. Digite **2003-01-10** para o valor de data de contratação.

### <a name="to-format-the-xml-document"></a>Para formatar o documento XML

1. Selecione o botão **Formatar documento** na barra de ferramentas do editor de XML.

     O documento XML é reformatado.

### <a name="to-save-the-xml-document"></a>Para salvar o documento XML

1. No menu **arquivo** , selecione **salvar como**.

     A caixa de diálogo **salvar arquivo como** é exibida. O nome de arquivo padrão é “XMLFile1”.

2. Insira o nome do arquivo e o local para o documento XML e clique em **salvar**.

## <a name="hiredatexsd-file"></a>hireDate.xsd Arquivo
 O seguinte arquivo de esquema é usado por passo a passo.

```
<?xml version="1.0"?>
<xs:schema attributeFormDefault="unqualified"
     elementFormDefault="qualified" targetNamespace="urn:empl-hire"
     xmlns:xs="http://www.w3.org/2001/XMLSchema">
  <xs:element name="employee">
    <xs:complexType>
      <xs:sequence>
        <xs:element name="ID" type="xs:unsignedShort" />
        <xs:element name="hire-date" type="xs:date" />
      </xs:sequence>
    </xs:complexType>
  </xs:element>
</xs:schema>
```

## <a name="see-also"></a>Consulte também
 [Editor de XML](../xml-tools/xml-editor.md)
