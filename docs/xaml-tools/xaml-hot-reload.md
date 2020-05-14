---
title: Escrever e depurar XAML usando XAML Hot Reload
description: XAML Hot Reload, ou XAML edit e continua, permite que você faça alterações no seu código XAML enquanto executa aplicativos
ms.date: 08/05/2019
ms.topic: conceptual
helpviewer_keywords:
- xaml edit and continue
- xaml hot reload
author: TerryGLee
ms.author: tglee
manager: jillfra
ms.technology: vs-ide-debug
ms.workload:
- multiple
ms.openlocfilehash: 120ae30b3a33a04f17bd2ec23b747ac41c9427cf
ms.sourcegitcommit: 5d1b2895d3a249c6bea30eb12b0ad7c0f0862d85
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2020
ms.locfileid: "80880089"
---
# <a name="write-and-debug-running-xaml-code-with-xaml-hot-reload-in-visual-studio"></a>Escreva e depurar o código XAML com XAML Hot Reload no Visual Studio

O XAML Hot Reload ajuda você a construir sua interface de usuário de aplicativo WPF ou UWP (UI) permitindo que você faça alterações no código XAML enquanto seu aplicativo está em execução. Hot Reload está disponível tanto no Visual Studio quanto no Blend para o Visual Studio. Esse recurso permite que você construa e teste gradualmente o código XAML com o benefício do contexto de dados, estado de autenticação e outra complexidade do mundo real que é difícil de simular durante o tempo de projeto. Se você precisar de ajuda para solucionar problemas XAML Hot Reload, consulte [Solução de problemas XAML Hot Reload](xaml-hot-reload-troubleshooting.md) em vez disso.

> [!NOTE]
> Se você estiver usando Xamarin.Forms, consulte [XAML Hot Reload for Xamarin.Forms](/xamarin/xamarin-forms/xaml/hot-reload).

XAML Hot Reload é especialmente útil nesses cenários:

* Corrigindo problemas de iu encontrados em seu código XAML depois que o aplicativo foi iniciado no modo de depuração.

* Construindo um novo componente de interface do bolso para um aplicativo que está em desenvolvimento, aproveitando o contexto de tempo de execução do seu aplicativo.

|Tipos de aplicativos suportados|Sistema Operacional e Ferramentas|
|-|-|-|
|Windows Presentation Foundation (WPF) |.NET Framework 4.6+ e .NET Core</br>Windows 7 e acima |
|Aplicativos Universais do Windows (UWP)|Windows 10 e acima, com o [Windows 10 SDK](https://developer.microsoft.com/windows/downloads/windows-10-sdk) 14393+ |

A ilustração a seguir mostra o uso da Árvore Visual Ao Vivo para abrir seu código-fonte e, em seguida, XAML Hot Reload para alterar o texto do botão e a cor do botão.

![Recarga Dinâmica de XAML](../debugger/media/xaml-hot-reload-using.gif)

> [!NOTE]
> Visual Studio XAML Hot Reload é atualmente suportado apenas ao executar seu aplicativo no Visual Studio ou Blend for Visual Studio com o depurador conectado **(F5** ou **Iniciar depuração).** Você não pode habilitar essa experiência usando [Attach to process](../debugger/attach-to-running-processes-with-the-visual-studio-debugger.md) a menos que você [defina manualmente uma variável de ambiente](xaml-hot-reload-troubleshooting.md#verify-that-you-use-start-debugging-rather-than-attach-to-process).

## <a name="known-limitations"></a>Limitações conhecidas

As seguintes limitações são conhecidas do XAML Hot Reload. Para contornar qualquer limitação que você encontrar, basta parar o depurador e, em seguida, concluir a operação.

|Limitações|WPF|UWP|Observações|
|-|-|-|-|
|Fiação de eventos para controles enquanto o aplicativo está em execução|Sem suporte|Sem suporte|Ver erro: *Garantir falha do evento*. Observe que no WPF você pode referenciar um manipulador de eventos existente. Nos aplicativos UWP, não é suportado o suporte a um manipulador de eventos existente.|
|Criando objetos de recursos em um dicionário de recursos, como aqueles na Página/Janela do seu aplicativo ou *app.xaml*|Suportado a partir do Visual Studio 2019 Update 2|Com suporte|Exemplo: adicionar `SolidColorBrush` a em um dicionário `StaticResource`de recursos para uso como um .</br>Nota: Recursos estáticos, conversores de estilo e outros elementos escritos em um dicionário de recursos podem ser aplicados/usados durante o uso do XAML Hot Reload. Apenas a criação do recurso não é suportada.</br> Alterando a `Source` propriedade do dicionário de recursos.|
|Adicionando novos controles, classes, janelas ou outros arquivos ao seu projeto enquanto o aplicativo está sendo executado|Sem suporte|Sem suporte|Nenhum|
|Gerenciamento de pacotes NuGet (adicionando/removendo/atualizando pacotes)|Sem suporte|Sem suporte|Nenhum|
|Alterando a vinculação de dados que usa a extensão de marcação {x:Bind}|N/D|Suportado a partir do Visual Studio 2019|Isso requer a versão 1809 do Windows 10 (build 10.0.17763). Não suportado no Visual Studio 2017 ou versões anteriores.|
|A alteração das diretivas x:Uid não é suportada|N/D|Sem suporte|Nenhum|
|Múltiplos processos | Sem suporte | Sem suporte | A recarga quente só pode ser usada contra 1 processo de cada vez. |

## <a name="error-messages"></a>Mensagens de erro

Você pode encontrar os seguintes erros ao usar o XAML Hot Reload.

|Mensagem de erro|Descrição|
|-|-|
|Garantir falha no evento|O erro indica que você está tentando conectar um evento a um de seus controles, que não é suportado enquanto seu aplicativo estiver em execução.|
|Esta alteração não é suportada pelo XAML Hot Reload e não será aplicada durante a sessão de depuração.|O erro indica que a alteração que você está tentando não é suportada pelo XAML Hot Reload. Interrompa a sessão de depuração, faça a alteração e, em seguida, reinicie a sessão de depuração. Se você encontrar um cenário sem suporte que você gostaria de ver suportado, use nossa nova opção "Sugerir um recurso" na [Comunidade de Desenvolvedores](https://developercommunity.visualstudio.com/spaces/8/index.html)do Visual Studio . |

## <a name="see-also"></a>Confira também

* [Solução de problemas de Recarga Dinâmica de XAML](xaml-hot-reload-troubleshooting.md)
* [Recarga quente xaml para xamarin.forms](/xamarin/xamarin-forms/xaml/hot-reload)
* [Editar e continuar (Visual C#)](../debugger/edit-and-continue-visual-csharp.md)
