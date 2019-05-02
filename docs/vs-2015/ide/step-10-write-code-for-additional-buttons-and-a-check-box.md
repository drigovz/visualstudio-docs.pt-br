---
title: 'Etapa 10: Escrever código para botões adicionais e uma caixa de seleção | Microsoft Docs'
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-general
ms.topic: conceptual
ms.assetid: 185cf370-ab39-4ac0-b6bc-601d5b95a4a2
caps.latest.revision: 23
author: gewarren
ms.author: gewarren
manager: jillfra
ms.openlocfilehash: 87c441271e72ef2aa67e0908e19473279f26ec53
ms.sourcegitcommit: 47eeeeadd84c879636e9d48747b615de69384356
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "63441942"
---
# <a name="step-10-write-code-for-additional-buttons-and-a-check-box"></a>Etapa 10: Escrever o código dos botões adicionais e de uma caixa de seleção
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Agora você está pronto para concluir os outros quatro métodos. Você pode copiar e colar esse código, mas se deseja saber a maioria deste tutorial, digite o código e use o IntelliSense.  
  
 Este código adiciona funcionalidades aos botões que você adicionou anteriormente. Sem esse código, os botões não fazem nada. Os botões usam o código em seus eventos de `Click` (e na caixa de seleção usa o evento de `CheckChanged`) para fazer coisas diferentes quando você ativa os controles. Por exemplo, o evento `clearButton_Click`, que é ativado quando você escolhe o botão **Limpar a imagem**, apaga a imagem atual configurando sua propriedade `Image` como `null` (ou `nothing`). Cada evento no código inclui comentários que explicam o que o código faz.  
  
 ![link para vídeo](../data-tools/media/playvideo.gif "PlayVideo")para uma versão em vídeo deste tópico, consulte [Tutorial 1: Criar um visualizador de imagens no Visual Basic – vídeo 5](http://go.microsoft.com/fwlink/?LinkId=205216) ou [Tutorial 1: Criar um visualizador de imagens em c# – vídeo 5](http://go.microsoft.com/fwlink/?LinkId=205206). Esses vídeos usam uma versão anterior do Visual Studio, portanto, existem pequenas diferenças em alguns comandos de menu e em outros elementos da interface do usuário. No entanto, os conceitos e procedimentos funcionam de maneiras semelhantes na versão atual do Visual Studio.  
  
> [!NOTE]
> Como uma melhor prática: Sempre comente o seu código. Os comentários são informações para uma pessoa ler e vale a pena tornar seu código mais legível. Todo em uma linha de comentário será ignorado pelo programa. No Visual C#, você comenta uma linha digitando duas barras no início (//) e no Visual Basic, você comenta uma linha iniciando-a com aspas simples (').  
  
### <a name="to-write-code-for-additional-buttons-and-a-check-box"></a>Para escrever códigos para botões adicionais e uma caixa de seleção  
  
- Adicione o seguinte código ao seu arquivo de código Form1 (Form1.cs ou Form1.vb). Escolha a guia **VB** para exibir o código do Visual Basic.  
  
     [!code-csharp[VbExpressTutorial1Step9_10#2](../snippets/csharp/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/cs/form1.cs#2)]
     [!code-vb[VbExpressTutorial1Step9_10#2](../snippets/visualbasic/VS_Snippets_VBCSharp/vbexpresstutorial1step9_10/vb/form1.vb#2)]  
  
### <a name="to-continue-or-review"></a>Para continuar ou revisar  
  
- Para ir para a próxima etapa do tutorial, confira [Etapa 11: Executar o programa e experimentar outros recursos](../ide/step-11-run-your-program-and-try-other-features.md).  
  
- Para retornar à etapa anterior do tutorial, confira [Etapa 9: Revisar, comentar e testar seu código](../ide/step-9-review-comment-and-test-your-code.md).
