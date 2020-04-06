---
title: Suporte para a janela de automóveis em um serviço de idioma legado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- language services [managed package framework], Autos window
- Autos window, supporting in language services [managed package framework]
ms.assetid: 47d40aae-7a3c-41e1-a949-34989924aefb
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 75f8c761721dde5dad4bb75b8675f71f678b06df
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704891"
---
# <a name="support-for-the-autos-window-in-a-legacy-language-service"></a>Suporte para a janela de automáticos em um serviço de linguagem herdado
A janela **Autos** exibe expressões como variáveis e parâmetros que estão no escopo quando o programa que está sendo depurado é pausado (seja devido a um ponto de ruptura ou uma exceção). As expressões podem incluir variáveis, locais ou globais, e parâmetros que foram alterados no âmbito local. A janela **Autos** também pode incluir instanciações de uma classe, estrutura ou algum outro tipo. Qualquer coisa que um avaliador de expressão possa avaliar pode ser potencialmente mostrado na janela **Autos.**

 O MPF (Managed Package Framework, quadro de pacotes gerenciados) não fornece suporte direto para a janela **Autos.** No entanto, se <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> você substituir o método, você pode retornar uma lista de expressões a serem apresentadas na janela **Autos.**

## <a name="implementing-support-for-the-autos-window"></a>Implementando suporte para a janela de automóveis
 Tudo o que você precisa fazer para apoiar <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> a <xref:Microsoft.VisualStudio.Package.LanguageService> janela **Autos** é implementar o método na classe. Sua implementação deve decidir, dada a localização no arquivo de origem, quais expressões devem aparecer na janela **Autos.** O método retorna uma lista de strings em que cada string representa uma única expressão. Um valor <xref:Microsoft.VisualStudio.VSConstants.S_OK> de retorno indica que a <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> lista contém expressões, enquanto indica que não há expressões para mostrar.

 As expressões reais retornadas são os nomes das variáveis ou parâmetros que aparecem naquele local no código. Esses nomes são passados ao avaliador de expressão para obter valores e tipos que são exibidos na janela **Autos.**

### <a name="example"></a>Exemplo
 O exemplo a seguir <xref:Microsoft.VisualStudio.Package.LanguageService.GetProximityExpressions%2A> mostra uma implementação do método <xref:Microsoft.VisualStudio.Package.LanguageService.ParseSource%2A> que obtém <xref:Microsoft.VisualStudio.Package.ParseReason>uma lista de expressões do método usando a razão da análise . Cada uma das expressões `TestVsEnumBSTR` é embrulhada como uma que implementa a <xref:Microsoft.VisualStudio.TextManager.Interop.IVsEnumBSTR> interface.

 Observe que `GetAutoExpressionsCount` `GetAutoExpression` os métodos e métodos são métodos personalizados no `TestAuthoringSink` objeto e foram adicionados para suportar este exemplo. Eles representam uma maneira pela qual `TestAuthoringSink` expressões adicionadas ao <xref:Microsoft.VisualStudio.Package.AuthoringSink.AutoExpression%2A> objeto pelo analisador (chamando o método) podem ser acessadas fora do analisador.

```csharp
using Microsoft.VisualStudio;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    public class TestLanguageService : LanguageService
    {
        public override int GetProximityExpressions(IVsTextBuffer buffer,
                                                    int line,
                                                    int col,
                                                    int cLines,
                                                    out IVsEnumBSTR ppEnum)
        {
            int retval = VSConstants.E_NOTIMPL;
            ppEnum = null;
            if (buffer != null)
            {
                IVsTextLines textLines = buffer as IVsTextLines;
                if (textLines != null)
                {
                    Source src = this.GetSource(textLines);
                    if (src != null)
                    {
                        TokenInfo tokenInfo = new TokenInfo();
                        string text = src.GetText();
                        ParseRequest req = CreateParseRequest(src,
                                                              line,
                                                              col,
                                                              tokenInfo,
                                                              text,
                                                              src.GetFilePath(),
                                                              ParseReason.Autos,
                                                              null);
                        req.Scope = this.ParseSource(req);
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;

                        retval = VSConstants.S_FALSE;
                        int spanCount = sink.GetAutoExpressionsCount();
                        if (spanCount > 0) {
                            TestVsEnumBSTR bstrList = new TestVsEnumBSTR();
                            for (int i = 0; i < spanCount; i++)
                            {
                                TextSpan span;
                                sink.GetAutoExpression(i, out span);
                                string expression = src.GetText(span.iStartLine,
                                                                span.iStartIndex,
                                                                span.iEndLine,
                                                                span.iEndIndex);
                                bstrList.AddString(expression);
                            }
                            ppEnum = bstrList;
                            retval = VSConstants.S_OK;
                        }
                    }
                }
            }
            return retval;
        }
    }
}
```
