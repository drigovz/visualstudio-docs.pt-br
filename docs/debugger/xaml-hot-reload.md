---
title: Gravar e depurar XAML usando o Hot recarregamento de XAML
description: O Hot recarregamento de XAML ou editar e continuar XAML permite que você faça alterações no código XAML durante a execução de aplicativos
ms.custom: ''
ms.date: 02/28/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: mikejo5000
ms.author: mikejo
manager: jillfra
ms.workload:
- multiple
ms.openlocfilehash: f1b2428024c30b8f96babf0cab6a56c60f52fa57
ms.sourcegitcommit: 3e74ec49a54e5c3da7631f4466128cdf4384af6b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/01/2019
ms.locfileid: "68711217"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Escrever e depurar o código XAML em execução com o Hot recarregamento de XAML no Visual Studio

O Hot recarregamento XAML do Visual Studio ajuda você a criar sua interface do usuário do aplicativo do WPF ou UWP, permitindo que você faça alterações no código XAML enquanto seu aplicativo está em execução. Esse recurso permite criar e testar incrementalmente o código XAML com o benefício do contexto de dados do aplicativo em execução, o estado de autenticação e outras complexidades do mundo real que são difíceis de simular durante o tempo de design.

O Hot recarregamento de XAML é especialmente útil nesses cenários:

* Correção de problemas de interface do usuário encontrados no código XAML depois que o aplicativo foi iniciado no modo de depuração.

* Criar um novo componente de interface do usuário para um aplicativo que está em desenvolvimento, aproveitando, ao mesmo tempo, o contexto do tempo de execução do aplicativo.

|Tipos de aplicativos com suporte|Sistema operacional e ferramentas|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6 ou versão posterior</br>Windows 7 e posterior |
|Aplicativos universais do Windows (UWP)|Windows 10 e posterior, com o [SDK do Windows 10](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393 + |

> [!NOTE]
> Atualmente, há suporte para o Hot recarregamento XAML do Visual Studio apenas ao executar o aplicativo no Visual Studio com o depurador anexado (**F5** ou **iniciar a depuração**). Você não pode habilitar essa experiência usando *anexar ao processo*.

## <a name="known-limitations"></a>Limitações conhecidas

Veja a seguir as limitações conhecidas do Hot recarregamento XAML. Para solucionar qualquer limitação que você encontrar, basta parar o depurador e concluir a operação.

|Limitação|WPF|UWP|Observações|
|-|-|-|-|
|Eventos de fiação para controles enquanto o aplicativo está em execução|Sem suporte|Sem suporte|Consulte o erro: *Verifique se o evento falhou*|
|Criando objetos de recurso em um dicionário de recursos, como aqueles na página/janela do seu aplicativo ou *app. XAML*|Sem suporte|Com suporte|Exemplo: adicionando um ```SolidColorBrush``` a um dicionário de recursos para uso como ```StaticResource```um.</br>Observação: Recursos estáticos, conversores de estilo e outros elementos gravados em um dicionário de recursos podem ser aplicados/usados ao usar o Hot recarregamento de XAML. Somente a criação do recurso não tem suporte.</br> Alterando a propriedade ```Source``` do dicionário de recursos.| 
|Adicionar novos controles, classes, janelas ou outros arquivos ao seu projeto enquanto o aplicativo está em execução|Sem suporte|Sem suporte|Nenhum|
|Gerenciando pacotes NuGet (adicionando/removendo/atualizando pacotes)|Sem suporte|Sem suporte|Nenhum|
|Alterando a associação de dados que usa a extensão de marcação {x:Bind}|N/D|Com suporte no Visual Studio 2019 e versões posteriores|Sem suporte no Visual Studio 2017 ou em versões anteriores|

## <a name="error-messages"></a>Mensagens de erro

Você pode se deparar com os seguintes erros ao usar o Hot recarregamento de XAML.

|Mensagem de erro|Descrição|
|-|-|-|
|Verifique se o evento falhou|Erro indica que você está tentando vincular um evento a um de seus controles, o que não tem suporte enquanto o aplicativo está em execução.|
|O XAML Edit and Continue não encontrou nenhum elemento a ser atualizado.|O erro ocorre quando você está editando XAML que o Hot reupload não pode atualizar em seu aplicativo.</br> Esse erro pode, às vezes, ser corrigido usando seu aplicativo em execução para navegar até uma exibição em que o XAML é usado.</br> Às vezes, esse erro significa que a alteração específica não pode ser aplicada até que você reinicie a sessão de depuração. |
|Não há suporte para essa alteração durante uma sessão de depuração.|Erro indica que a alteração que você está tentando executar não é suportada pelo Hot recarregamento XAML. Pare a sessão de depuração, faça a alteração e reinicie a sessão de depuração.|
