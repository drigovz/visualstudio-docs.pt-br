---
title: Manipulação de erros e valores de devolução | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- errors [Visual Studio SDK], handling
- error handling
- return values
ms.assetid: b2d9079d-39a6-438a-8010-290056694b5c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 30b6b9bff9056360f9ea840f47b1488f05bee872
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80711931"
---
# <a name="error-handling-and-return-values"></a>Manipulação de erros e valores de devolução
VSPackages e COM usam a mesma arquitetura para erros. As `SetErrorInfo` `GetErrorInfo` funções fazem parte da interface de programação de aplicativos Win32 (API). Qualquer VSPackage no ambiente de desenvolvimento integrado (IDE) pode chamar essas APIs globais do Win32 para registrar informações de erro ricas ao receber uma notificação de erro. Os [!INCLUDE[vsipsdk](../extensibility/includes/vsipsdk_md.md)] conjuntos interop fornecem para gerenciar informações de erro.

## <a name="interop-methods"></a>Métodos interop
 Como conveniência, o IDE fornece <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>um método, para usar em vez de chamar as APIs win32. No uso gerenciado <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A>de código . Quando um `HRESULT` erro chega ao nível em que a mensagem de erro <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget> deve ser exibida (este <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A>é muitas vezes o objeto que implementa um manipulador de comando), o IDE usa outro método, para exibir a caixa de mensagens apropriada. No código gerenciado <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> use o método.

 Como um implementador DE PACOTES `ISupportErrorInfo`VS, seus objetos COM normalmente implementam . A `ISupportErrorInfo` interface garante que informações ricas de erros possam mover-se verticalmente até a cadeia de chamadas. Objetos que podem ser usados em `ISupportErrorInfo` processos ou em todos os segmentos devem ser suportados para garantir que as informações de erro ricas sejam adequadamente remanejarem de volta ao chamador.

 Todos os objetos relacionados ao VSPackages e que estão envolvidos na extensão do IDE, incluindo fábricas de editores, editores, hierarquias e serviços oferecidos, devem suportar informações ricas de erros. Embora o IDE não exija que `ISupportErrorInfo`esses objetos VSPackage sejam implementados, ele é sempre encorajado.

 O IDE é responsável por reportar informações de [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] erro `HRESULT` e exibi-la a um usuário sempre que uma é propagada para o IDE. O IDE também é `ErrorInfo` o mecanismo para criar objetos.

## <a name="general-guidelines"></a>Diretrizes gerais
 Você pode <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> usar <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> os métodos e métodos para definir e relatar erros que são internos à sua implementação do VSPackage também. No entanto, como regra geral, siga estas diretrizes para lidar com mensagens de erro em seu VSPackage:

- Implemente `ISupportErrorInfo` em seus objetos VSPackage COM.

- Crie um mecanismo de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> relatório de erro <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>que chama o método em objetos que implementam .

- Deixe o IDE exibir erros <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> aos usuários através do método.

## <a name="error-information-in-the-ide"></a>Informações de erro no IDE
 As seguintes regras indicam como [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)] lidar com informações de erro no IDE:

- Como estratégia defensiva para garantir que informações de erro obsoletas não sejam relatadas aos usuários, as funções que chamam o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.ReportErrorInfo%2A> método devem primeiro chamar o <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> método. Passe `null` para limpar mensagens de erro armazenadas em cache antes de chamar qualquer coisa que possa definir novas informações de erro.

- Funções que não reportam diretamente mensagens de <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> erro só podem ligar `HRESULT`para o método se estiverem retornando um erro . É permitido limpar a `ErrorInfo` entrada de uma função ou <xref:Microsoft.VisualStudio.VSConstants.S_OK>ao retornar. A única exceção a esta regra `HRESULT` é quando uma chamada retorna um erro do qual a parte receptora pode explicitamente recuperar ou ignorar com segurança.

- Qualquer parte que ignorar explicitamente `HRESULT` um <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> erro <xref:Microsoft.VisualStudio.VSConstants.S_OK>deve chamar o método com . Caso contrário, `ErrorInfo` o objeto pode ser usado acidentalmente quando `ErrorInfo`outra parte gera um erro sem fornecer o seu próprio .

- Todos os métodos `HRESULT` que originam um <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> erro são encorajados a chamar o método para fornecer informações ricas de erro. Se o `HRESULT` retornado `FACILITY_ITF` for um erro especial, então `ErrorInfo`o método é necessário para fornecer um objeto adequado. Se o erro retornado for um erro <xref:Microsoft.VisualStudio.VSConstants.E_OUTOFMEMORY> <xref:Microsoft.VisualStudio.VSConstants.E_ABORT>padrão <xref:Microsoft.VisualStudio.VSConstants.E_INVALIDARG> <xref:Microsoft.VisualStudio.VSConstants.E_UNEXPECTED>do sistema (por exemplo, , , , e assim por <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> diante.) é aceitável retornar o código de erro sem chamar explicitamente o método. Como estratégia de codificação defensiva, `HRESULT` ao originar um <xref:Microsoft.VisualStudio.Shell.Interop.IVsUIShell.SetErrorInfo%2A> erro (incluindo `ErrorInfo` erros do sistema), sempre `null`chame o método, seja com a descrição da falha com mais detalhes, ou .

- Todas as funções que retornam um erro originado por outra chamada devem `HRESULT` passar as `ErrorInfo` informações recebidas da chamada falha no sem modificar o objeto.

## <a name="see-also"></a>Confira também
- <xref:Microsoft.VisualStudio.OLE.Interop.IOleCommandTarget>
- [SetErrorInfo (Automação de componentes)](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-seterrorinfo)
- [GetErrorInfo](/previous-versions/windows/desktop/api/oleauto/nf-oleauto-geterrorinfo)
- [ISupportErrorInfo Interface](/previous-versions/windows/desktop/api/oaidl/nn-oaidl-isupporterrorinfo)
