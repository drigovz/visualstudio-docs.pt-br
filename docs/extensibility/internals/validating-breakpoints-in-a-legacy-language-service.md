---
title: Validando pontos de interrupção em um serviço de idioma legado | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- breakpoint validation
- language services [managed package framework], breakpoint validation
ms.assetid: a7e873cd-dfe1-474f-bda5-fd7532774b15
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: af09e4f8f2156100bea9267c92ffebeb64ce1aa3
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80704093"
---
# <a name="validating-breakpoints-in-a-legacy-language-service"></a>Validando pontos de interrupção em um serviço de linguagem herdado
Um ponto de ruptura indica que a execução do programa deve parar em um determinado ponto enquanto ela está sendo executada em um depurador. Um usuário pode colocar um ponto de ruptura em qualquer linha no arquivo de origem, já que o editor não tem conhecimento do que constitui um local válido para um ponto de ruptura. Quando o depurador é lançado, todos os pontos de interrupção marcados (chamados de pontos de interrupção pendentes) são vinculados ao local apropriado no programa em execução. Ao mesmo tempo, os pontos de interrupção são validados para garantir que eles marquem locais de código válidos. Por exemplo, um ponto de ruptura em um comentário não é válido, porque não há código nesse local no código-fonte. O depurador desativa pontos de interrupção inválidos.

 Como o serviço de idiomas sabe sobre o código-fonte que está sendo exibido, ele pode validar pontos de interrupção antes que o depurador seja lançado. Você pode substituir <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> o método para retornar um período especificando um local válido para um ponto de ruptura. O local do ponto de interrupção ainda é validado quando o depurador é lançado, mas o usuário é notificado de pontos de interrupção inválidos sem esperar que o depurador seja carregado.

## <a name="implementing-support-for-validating-breakpoints"></a>Implementando suporte para validação de pontos de interrupção

- O <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> método é dada a posição do ponto de ruptura. Sua implementação deve decidir se o local é válido ou não e indicar isso retornando um período de texto que identifica o código associado à posição de linha do ponto de ruptura.

- Retorne <xref:Microsoft.VisualStudio.VSConstants.S_OK> se o local <xref:Microsoft.VisualStudio.VSConstants.S_FALSE> for válido ou se não for válido.

- Se o ponto de ruptura for válido, o período de texto será destacado juntamente com o ponto de ruptura.

- Se o ponto de ruptura for inválido, uma mensagem de erro será exibida na barra de status.

### <a name="example"></a>Exemplo
 Este exemplo mostra uma <xref:Microsoft.VisualStudio.Package.LanguageService.ValidateBreakpointLocation%2A> implementação do método que chama o analisador para obter o intervalo de código (se houver) no local especificado.

 Este exemplo assume que você `GetCodeSpan` adicionou <xref:Microsoft.VisualStudio.Package.AuthoringSink> um método à classe `true` que valida o período de texto e retorna se for um local de ponto de ruptura válido.

```csharp
using Microsoft VisualStudio;
using Microsoft.VisualStudio.Package;
using Microsoft.VisualStudio.TextManager.Interop;

namespace TestLanguagePackage
{
    class TestLanguageService : LanguageService
    {
        public override int ValidateBreakpointLocation(IVsTextBuffer buffer,
                                                       int line,
                                                       int col,
                                                       TextSpan[] pCodeSpan)
        {
            int retval = VSConstants.S_FALSE;
            if (pCodeSpan != null)
            {
                // Initialize span to current line by default.
                pCodeSpan[0].iStartLine = line;
                pCodeSpan[0].iStartIndex = col;
                pCodeSpan[0].iEndLine = line;
                pCodeSpan[0].iEndIndex = col;
            }

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
                                                              ParseReason.CodeSpan,
                                                              null);
                        req.Scope = this.ParseSource(req);
                        TestAuthoringSink sink = req.Sink as TestAuthoringSink;

                        TextSpan span = new TextSpan();
                        if (sink.GetCodeSpan(out span))
                        {
                            pCodeSpan[0] = span;
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

## <a name="see-also"></a>Confira também
- [Recursos do serviço de linguagem herdado](../../extensibility/internals/legacy-language-service-features1.md)
