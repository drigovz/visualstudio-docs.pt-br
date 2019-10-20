---
title: Personalizar como o Visual Studio 2015 cria legendas para controles vinculados a dados | Microsoft Docs
titleSuffix: ''
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-data-tools
ms.topic: conceptual
dev_langs:
- VB
- CSharp
- C++
- aspx
helpviewer_keywords:
- Label captions, Data Sources window
- smart captions
- captions, data-bound
- Data Sources Window, label captions
ms.assetid: 6d4d15f8-4d78-42fd-af64-779ae98d62c8
caps.latest.revision: 15
author: jillre
ms.author: jillfra
manager: jillfra
ms.openlocfilehash: 04f32fa0426039f50c0a0352ef0b04900d705a98
ms.sourcegitcommit: a8e8f4bd5d508da34bbe9f2d4d9fa94da0539de0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/19/2019
ms.locfileid: "72657436"
---
# <a name="customize-how-visual-studio-creates-captions-for-data-bound-controls"></a>Personalizar como o Visual Studio cria legendas para controles associados a dados
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Quando você arrasta itens da [janela fontes de dados](https://msdn.microsoft.com/library/0d20f699-cc95-45b3-8ecb-c7edf1f67992) para a designer de formulários do Windows, uma consideração especial entra em cena: os nomes de coluna nos rótulos de legenda são reformatados em uma cadeia de caracteres mais legível quando duas ou mais palavras são encontradas como concatenadas Unido. Você pode personalizar a maneira como esses rótulos são criados, definindo os valores **SmartCaptionExpression**, **SmartCaptionReplacement**e **SmartCaptionSuffix** no **HKEY_CURRENT_USER\Software\Microsoft\VisualStudio\ 10.0 \** chave do registro de data designers.

> [!NOTE]
> Essa chave do registro não existe até que você a crie.

 A legenda inteligente é controlada pela expressão regular inserida no valor do valor **SmartCaptionExpression** . A adição da chave do registro dos **Data designers** substitui a expressão regular padrão que controla os rótulos de legenda. Para obter mais informações sobre expressões regulares, consulte [usando expressões regulares no Visual Studio](../ide/using-regular-expressions-in-visual-studio.md).

 A tabela a seguir descreve os valores de registro que controlam os rótulos de legenda.

|Item do registro|Descrição|
|-------------------|-----------------|
|**SmartCaptionExpression**|A expressão regular usada para corresponder seus padrões.|
|**SmartCaptionReplacement**|O formato para exibir todos os grupos correspondentes na **SmartCaptionExpression**.|
|**SmartCaptionSuffix**|Uma cadeia de caracteres opcional a ser acrescentada ao final da legenda.|

 A tabela a seguir lista as configurações padrão internas para esses valores de registro.

|Item do registro|Valor padrão|Explicação|
|-------------------|-------------------|-----------------|
|**SmartCaptionExpression**|(\\ \p{Ll}) (\\ \p{Lu}) &#124;_+|Corresponde a um caractere minúsculo seguido por um caractere maiúsculo ou um sublinhado.|
|**SmartCaptionReplacement**|$1 $2|O $1 representa os caracteres correspondentes nos primeiros parênteses da expressão, e o $2 representa os caracteres correspondidos no segundo parênteses. A substituição é a primeira correspondência, um espaço e a segunda correspondência.|
|**SmartCaptionSuffix**|:|Representa um caractere acrescentado à cadeia de caracteres retornada. Por exemplo, se a legenda for `Company Name`, o sufixo a tornará `Company Name:`|

> [!CAUTION]
> Você deve ter muito cuidado ao fazer qualquer coisa no editor do registro. Faça backup do registro antes de editá-lo. Se você usar o editor do registro incorretamente, poderá causar sérios problemas que podem exigir a reinstalação do sistema operacional. A Microsoft não garante que os problemas que você causa usando o editor do registro incorretamente possam ser resolvidos. Use o Editor do Registro por sua conta e risco.
>
> O artigo da base de conhecimento a seguir contém instruções para fazer backup, editar e restaurar o registro: [Descrição do registro do Microsoft Windows](http://support.microsoft.com/default.aspx?scid=kb;en-us;256986) (http://support.microsoft.com/default.aspx?scid=kb; en-us; 256986)

### <a name="to-modify-the-smart-captioning-behavior-of-the-data-sources-window"></a>Para modificar o comportamento de legenda inteligente da janela fontes de dados

1. Abra uma janela de comando clicando em **Iniciar** e em **executar**.

2. Digite `regedit` na caixa de diálogo **executar** e clique em **OK**.

3. Expanda o nó **HKEY_CURRENT_USER** .

4. Expanda o nó **software** .

5. Expanda o nó **Microsoft** .

6. Expanda o nó **VisualStudio** .

7. Clique com o botão direito do mouse no nó **10,0** e crie uma nova **chave** chamada `Data Designers`.

8. Clique com o botão direito do mouse no nó **Data designers** e crie um novo **valor de cadeia de caracteres** chamado `SmartCaptionExpression`.

9. Clique com o botão direito do mouse no nó **Data designers** e crie um novo **valor de cadeia de caracteres** chamado `SmartCaptionReplacement`.

10. Clique com o botão direito do mouse no nó **Data designers** e crie um novo **valor de cadeia de caracteres** chamado `SmartCaptionSuffix`.

11. Clique com o botão direito do mouse no item **SmartCaptionExpression** e selecione **Modificar**.

12. Insira a expressão regular que você deseja que a janela **fontes de dados** use.

13. Clique com o botão direito do mouse no item **SmartCaptionReplacement** e selecione **Modificar**.

14. Insira a cadeia de caracteres de substituição formatada da maneira que você deseja exibir os padrões correspondentes em sua expressão regular.

15. Clique com o botão direito do mouse no item **SmartCaptionSuffix** e selecione **Modificar**.

16. Insira os caracteres que você deseja que apareçam no final da legenda.

     Na próxima vez que você arrastar itens da janela **fontes de dados** , os rótulos de legenda serão criados usando os novos valores de registro fornecidos.

### <a name="to-turn-off-the-smart-captioning-feature"></a>Para desativar o recurso de legenda inteligente

1. Abra uma janela de comando clicando em **Iniciar** e em **executar**.

2. Digite `regedit` na caixa de diálogo **executar** e clique em **OK**.

3. Expanda o nó **HKEY_CURRENT_USER** .

4. Expanda o nó **software** .

5. Expanda o nó **Microsoft** .

6. Expanda o nó **VisualStudio** .

7. Clique com o botão direito do mouse no nó **10,0** e crie uma nova **chave** chamada `Data Designers`.

8. Clique com o botão direito do mouse no nó **Data designers** e crie um novo **valor de cadeia de caracteres** chamado `SmartCaptionExpression`.

9. Clique com o botão direito do mouse no nó **Data designers** e crie um novo **valor de cadeia de caracteres** chamado `SmartCaptionReplacement`.

10. Clique com o botão direito do mouse no nó **Data designers** e crie um novo **valor de cadeia de caracteres** chamado `SmartCaptionSuffix`.

11. Clique com o botão direito do mouse no item **SmartCaptionExpression** e selecione **Modificar**.

12. Insira `(.*)` para o valor. Isso corresponderá à cadeia de caracteres inteira.

13. Clique com o botão direito do mouse no item **SmartCaptionReplacement** e selecione **Modificar**.

14. Insira `$1` para o valor. Isso substitui a cadeia de caracteres pelo valor correspondente, que é a cadeia de caracteres inteira para que ela permaneça inalterada.

     Na próxima vez que você arrastar itens da janela **fontes de dados** , os rótulos de legenda serão criados com legendas não modificadas.

## <a name="see-also"></a>Consulte também
 [Associar controles a dados no Visual Studio](../data-tools/bind-controls-to-data-in-visual-studio.md)
