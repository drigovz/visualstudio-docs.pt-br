---
title: Obtendo um Porto | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- ports, getting
- debugging [Debugging SDK], ports
ms.assetid: 745c2337-cfff-4d02-b49c-3ca7c4945c5e
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7bf4948e7cb2590136774eab76fbafec91dbfa40
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80738634"
---
# <a name="get-a-port"></a>Obter uma porta
Uma porta representa uma conexão com uma máquina em que os processos estão sendo executados. Essa máquina pode ser a máquina local ou uma máquina remota (que poderia estar executando um sistema operacional não baseado no Windows; consulte [Portas](../../extensibility/debugger/ports.md) para obter mais informações).

Uma porta é representada pela interface [IDebugPort2.](../../extensibility/debugger/reference/idebugport2.md) Ele é usado para obter informações sobre processos em execução na máquina à que a porta está conectada.

Um mecanismo de depuração precisa ter acesso a uma porta para registrar os nódulos do programa com a porta e satisfazer solicitações de informações do processo. Por exemplo, se o mecanismo de depuração implementar a interface [IDebugProgramProvider2,](../../extensibility/debugger/reference/idebugprogramprovider2.md) a implementação do método [GetProviderProcessData](../../extensibility/debugger/reference/idebugprogramprovider2-getproviderprocessdata.md) poderá solicitar à porta que as informações necessárias do processo sejam devolvidas.

O Visual Studio fornece a porta necessária para o motor de depuração, e obtém esta porta de um fornecedor de porta. Se um programa for anexado (seja dentro do depurador ou por causa de uma exceção, que aciona a caixa de diálogo Just-in-Time [JIT]), o usuário será escolhido para usar (outro nome para um fornecedor de porta) para usar. Caso contrário, se o usuário iniciar o programa de dentro do depurador, o sistema do projeto especificar o fornecedor de porta a ser usado. Em ambos os casoes, o Visual Studio instancia o fornecedor de portas, representado por uma interface [IDebugPortSupplier2,](../../extensibility/debugger/reference/idebugportsupplier2.md) e pede uma nova porta ligando para [AddPort](../../extensibility/debugger/reference/idebugportsupplier2-addport.md) com uma interface [IDebugPortRequest2.](../../extensibility/debugger/reference/idebugportrequest2.md) Esta porta é então transmitida para o motor de depuração de uma forma ou de outra.

## <a name="example"></a>Exemplo
Este fragmento de código mostra como usar a porta fornecida ao [LaunchSuspended](../../extensibility/debugger/reference/idebugenginelaunch2-launchsuspended.md) para registrar um nó de programa no [ResumeProcess](../../extensibility/debugger/reference/idebugenginelaunch2-resumeprocess.md). Parâmetros não diretamente relacionados a esse conceito foram omitidos para clareza.

> [!NOTE]
> Este exemplo usa a porta para iniciar e retomar o processo e assume que a interface [IDebugPortEx2](../../extensibility/debugger/reference/idebugportex2.md) é implementada na porta. Esta não é de forma alguma a única maneira de executar essas tarefas, e é possível que a porta não esteja envolvida além de ter o [IDebugProgramNode2](../../extensibility/debugger/reference/idebugprogramnode2.md) do programa dado a ele.

```cpp
// This is an IDebugEngineLaunch2 method.
HRESULT CDebugEngine::LaunchSuspended(/* omitted parameters */,
                                      IDebugPort2 *pPort,
                                      /* omitted parameters */,
                                      IDebugProcess2**ppDebugProcess)
{
    // do stuff here to set up for a launch (such as handling the other parameters)
    ...

    // Now get the IPortNotify2 interface so we can register a program node
    // in CDebugEngine::ResumeProcess.
    CComPtr<IDebugDefaultPort2> spDefaultPort;
    HRESULT hr = pPort->QueryInterface(&spDefaultPort);
    if (SUCCEEDED(hr))
    {
        CComPtr<IDebugPortNotify2> spPortNotify;
        hr = spDefaultPort->GetPortNotify(&spPortNotify);
        if (SUCCEEDED(hr))
        {
            // Remember the port notify so we can use it in ResumeProcess.
            m_spPortNotify = spPortNotify;

            // Now launch the process in a suspended state and return the
            // IDebugProcess2 interface
            CComPtr<IDebugPortEx2> spPortEx;
            hr = pPort->QueryInterface(&spPortEx);
            if (SUCCEEDED(hr))
            {
                // pass on the parameters we were given (omitted here)
                hr = spPortEx->LaunchSuspended(/* omitted parameters */,ppDebugProcess)
            }
        }
    }
    return(hr);
}

HRESULT CDebugEngine::ResumeProcess(IDebugProcess2 *pDebugProcess)
{
    // Make a program node for this process
    HRESULT hr;
    CComPtr<IDebugProgramNode2> spProgramNode;
    hr = this->GetProgramNodeForProcess(pProcess, &spProgramNode);
    if (SUCCEEDED(hr))
    {
        hr = m_spPortNotify->AddProgramNode(spProgramNode);
        if (SUCCEEDED(hr))
        {
            // resume execution of the process using the port given to us earlier.
            // (Querying for the IDebugPortEx2 interface is valid here since
            // that's how we got the IDebugPortNotify2 interface in the first place.)
            CComPtr<IDebugPortEx2> spPortEx;
            hr = m_spPortNotify->QueryInterface(&spPortEx);
            if (SUCCEEDED(hr))
            {
                hr = spPortEx->ResumeProcess(pDebugProcess);
            }
        }
    }
    return(hr);
}
```

## <a name="see-also"></a>Confira também
- [Registrando o programa](../../extensibility/debugger/registering-the-program.md)
- [Permitindo que um programa seja depurado](../../extensibility/debugger/enabling-a-program-to-be-debugged.md)
- [Fornecedores portuários](../../extensibility/debugger/port-suppliers.md)
- [Portas](../../extensibility/debugger/ports.md)
