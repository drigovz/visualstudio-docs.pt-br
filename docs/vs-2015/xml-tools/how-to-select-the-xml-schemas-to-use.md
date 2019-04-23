---
title: 'Como: Selecione os esquemas XML para usar | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-xml-tools
ms.topic: conceptual
ms.assetid: d6fda3ef-d465-4788-8514-2f2d528d658c
caps.latest.revision: 8
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 7f8e3f4d53b0a8b79367064761ba0fc5b901dc5e
ms.sourcegitcommit: 53aa5a413717a1b62ca56a5983b6a50f7f0663b3
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/17/2019
ms.locfileid: "59670063"
---
# <a name="how-to-select-the-xml-schemas-to-use"></a>Como: Selecionar os esquemas XML que serão usados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

O editor XML fornece um cache de esquema %InstallDir% localizado no diretório \ \ esquemas XML. O cache de esquema inclui esquemas XML conhecidos que são usados para validação do IntelliSense e de documento XML.  
  
 O **esquemas** propriedade do documento é usada para selecionar um ou mais XML esquemas definição de esquema XSD (linguagem) para usar. Permite que você selecionar esquemas de cache do esquema, ou especifica um esquema que não está localizado no cache.  
  
 Os esquemas que você especifica são salvos no arquivo oculto opções de usuário de solução (.sln), junto com quaisquer propriedades restantes de documento XML. Como resultado, você não tem que digitar novamente esses valores na próxima vez que você abrir a solução.  
  
> [!NOTE]
>  O editor pode validar usando um esquema embutido, ou um esquema referenciado pelo atributo de `xsd:schemaLocation` . Para obter mais informações, consulte [validação de documento XML](../xml-tools/xml-document-validation.md).  
  
### <a name="to-select-an-xml-schema-from-the-schema-cache"></a>Para selecionar um esquema XML de cache do esquema  
  
1. Abrir um arquivo no editor XML.  
  
2. Na janela de propriedades do documento, clique no botão sobre a **esquemas** campo.  
  
    O **esquemas XML** caixa de diálogo é exibida. A caixa de diálogo lista todos os esquemas com uma extensão. xsd no cache de esquema (incluindo Esquemas referenciados no arquivo de Catalog.) e também qualquer esquema que está na solução atual, abra no Visual Studio, referenciado em um `xsd:schemaLocation` de atributo ou referenciados em o **esquemas** propriedade.  
  
3. Selecione os esquemas para usar a validação seguindo um destes procedimentos:  
  
   - Selecione um esquema listado na **esquemas XML** caixa de diálogo, clique o **uso** coluna e, em seguida, selecione **usar este esquema**.  
  
     - ou -  
  
   - Selecione vários esquemas listados na **esquemas XML** caixa de diálogo, o botão direito do mouse e selecione **usar este esquema**.  
  
4. Clique em **OK**.  
  
    A lista de esquemas selecionados será copiada para o **esquemas** propriedade de documento.  
  
### <a name="to-add-an-xml-schema-to-the-schema-cache"></a>Para adicionar um esquema XML para o cache de esquema  
  
1.  Na janela de propriedades do documento, clique no botão sobre a **esquemas** campo.  
  
2.  Clique em **Adicionar**.  
  
     Isso abre o **abrir esquema XSD** caixa de diálogo.  
  
3.  Procurar e selecione os esquemas para adicionar ao cache de esquema.  
  
4.  Clique em **Abrir**.  
  
     Os esquemas adicionados ao esquema armazenam em cache e é o **uso** o valor da coluna é definido como **usar este esquema**.  
  
### <a name="to-delete-an-xml-schema-from-the-schema-cache"></a>Para excluir um esquema XML de cache do esquema  
  
1.  Na janela de propriedades do documento, clique no botão sobre a **esquemas** campo.  
  
2.  Selecione o esquema para remover e, em seguida, clique em **remover**.  
  
     O esquema é removido do cache de memória do esquema, mas não é removido do sistema de arquivos.  
  
    > [!NOTE]
    >  Se você ainda terá uma referência para o esquema por meio de um `schemaLocation` atributo ou uma correspondência `targetNamespace` , em seguida, **remover** não funcionará nesta situação devido à associação automática. Nesse caso, é recomendável que você marca o esquema como **não use esquemas selecionados** na **usar** coluna.  
  
## <a name="see-also"></a>Consulte também  
 [Cache de esquema](../xml-tools/schema-cache.md)   
 [Caixa de diálogo de esquemas XML](../xml-tools/xml-schemas-dialog-box.md)   
 [Editor de XML](../xml-tools/xml-editor.md)
