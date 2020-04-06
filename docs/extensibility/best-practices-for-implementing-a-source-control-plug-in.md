---
title: Práticas recomendadas para implementar um plug-in de controle de fonte | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- source control plug-ins, best practices
- best practices, source control plug-ins
- source control [Visual Studio SDK], plug-ins
ms.assetid: 85e73b73-29dc-464f-8734-ed308742c435
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 68491f22d63ae3ebb664b7c22188a661dccbf39a
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80740047"
---
# <a name="best-practices-for-implementing-a-source-control-plug-in"></a>Práticas recomendadas para implementar um plug-in de controle de origem
Os seguintes detalhes técnicos podem ajudá-lo [!INCLUDE[vsprvs](../code-quality/includes/vsprvs_md.md)]a implementar de forma confiável um plug-in de controle de origem .

## <a name="memory-management-issues"></a>Problemas de gerenciamento de memória
 Na maioria dos casos, o ambiente de desenvolvimento integrado (IDE), que é o chamador, libera e aloca a memória. O plug-in de controle de origem retorna strings e outros itens em buffers alocados pelo chamador. Exceções são observadas nas descrições de funções específicas onde ocorrem.

## <a name="arrays-of-file-names"></a>Matrizes de nomes de arquivos
 Quando uma matriz de arquivos é aprovada, ela não é aprovada como uma matriz contígua de nomes de arquivos. Ele é passado como uma matriz de ponteiros para nomes de arquivos. Por exemplo, no [SccGet,](../extensibility/sccget-function.md)os nomes `lpFileNames` dos arquivos `lpFileNames` são passados pelo `char **`parâmetro, onde na verdade é um ponteiro para um . `lpFileNames`[0] é um ponteiro para `lpFileNames`o primeiro nome, [1] é um ponteiro para o segundo nome, e assim por diante.

## <a name="large-model"></a>Modelo grande
 Todos os ponteiros são de 32 bits, mesmo em sistemas operacionais de 16 bits.

## <a name="fully-qualified-paths"></a>Caminhos totalmente qualificados
 Quando os nomes de arquivos ou diretórios são especificados como argumentos, eles devem ser caminhos totalmente qualificados ou caminhos UNC, sem os retrocessos finais. É responsabilidade do plug-in de controle de origem traduzi-los para caminhos relativos, se esse for um requisito do sistema de controle de origem subjacente.

## <a name="specify-a-fully-qualified-path-for-the-registered-dll"></a>Especifique um caminho totalmente qualificado para a DLL registrada
 O IDE não carrega mais DLLs de caminhos relativos (por exemplo, *.\NewProvider.dll*). Um caminho completo da DLL deve ser especificado (por exemplo, *C:\Providers\NewProvider.dll*). Essa exigência reforça a segurança do IDE, impedindo o carregamento de DLLs de controle de origem não autorizados ou personificados.

## <a name="check-for-an-existing-vssci-plug-in-when-you-install-your-source-control-plug-in"></a>Verifique se há um plug-in VSSCI existente quando você instala seu plug-in de controle de origem
 Um usuário que planeja instalar seu plug-in de controle de origem pode já ter um plug-in de controle de origem existente instalado no computador. O programa de instalação (configuração) do plug-in que você cria deve determinar se existem valores existentes para as chaves de registro relevantes. Se essas chaves já estiverem definidas, seu programa de instalação deve perguntar ao usuário se deve registrar seu plug-in como o plug-in padrão de controle de origem e substituir o que já está instalado.

## <a name="error-result-codes-and-reporting"></a>Códigos de resultados de erro e relatórios
 O `SCC_OK` código de retorno de uma função de controle de origem indica que a operação foi bem sucedida para todos os arquivos. Se a operação falhar, espera-se que retorne o último código de erro encontrado.

 A regra para a emissão de relatórios é que, se ocorrer um erro no IDE, o IDE é responsável por reportá-lo. Se ocorrer um erro no sistema de controle de origem, o plug-in de controle de origem é responsável por reportá-lo. Por exemplo, **nenhum arquivo selecionado no momento** seria relatado pelo IDE, enquanto este arquivo já está **verificado** seria relatado pelo plug-in.

## <a name="the-context-structure"></a>A estrutura do contexto
 Durante a chamada para o [SccInitialize,](../extensibility/sccinitialize-function.md)o chamador passa o `ppvContext` parâmetro, que é uma alça não inicializada para um vazio. O plug-in de controle de origem pode ignorar esse parâmetro ou pode alocar uma estrutura de qualquer tipo e colocar um ponteiro nessa estrutura no ponteiro passado. O IDE não entende essa estrutura, mas passa um ponteiro para esta estrutura em todas as outras chamadas no plug-in. Isso fornece informações valiosas de cache de contexto para o plug-in que ele pode usar para manter informações de estado global que persistem em chamadas de função sem usar variáveis globais. O plug-in é responsável por liberar a estrutura em uma chamada para o [SccUninitialize](../extensibility/sccuninitialize-function.md).

 Se o plug-in `SCC_CAP_REENTRANT` definir o bit no [SccInitialize](../extensibility/sccinitialize-function.md) (especificamente, no `lpSccCaps` parâmetro), várias estruturas de contexto serão usadas para rastrear todos os projetos que estão abertos.

## <a name="bitflags-and-other-command-options"></a>Bitflags e outras opções de comando
 Para cada comando, como o [SccGet,](../extensibility/sccget-function.md)o IDE pode especificar muitas opções que alteram o comportamento do comando.

 A API suporta a definição de certas opções pelo IDE através do `fOptions` parâmetro. Essas opções são descritas em [Bitflags usadas por comandos específicos,](../extensibility/bitflags-used-by-specific-commands.md) juntamente com os comandos que afetam. Em geral, essas são opções para as quais o usuário não seria solicitado.

 A maioria das opções de configuração configuráveis pelo usuário não são definidas dessa maneira, porque variam amplamente entre os plug-ins de controle de origem. Portanto, o mecanismo recomendado é um botão **Avançado.** Por exemplo, na caixa de diálogo **Obter,** o IDE exibe apenas informações que ele entende, mas também exibe um botão **Avançado** se o plug-in tiver opções para este comando. Quando o usuário clica no botão **Avançado,** o IDE chama as [Opções de Comando sccGetpara](../extensibility/sccgetcommandoptions-function.md) ativar o plug-in de controle de origem para solicitar informações ao usuário, como bitflags ou data/hora. O plug-in retorna essas informações em uma `SccGet` estrutura que é passada para trás durante o comando.

## <a name="see-also"></a>Confira também
- [Plug-ins de controle de origem](../extensibility/source-control-plug-ins.md)
- [Criar um plug-in de controle de origem](../extensibility/internals/creating-a-source-control-plug-in.md)
