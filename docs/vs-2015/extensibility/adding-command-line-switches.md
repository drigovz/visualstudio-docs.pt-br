---
title: Adicionando opções de linha de comando | Microsoft Docs
ms.date: 11/15/2016
ms.prod: visual-studio-dev14
ms.technology: vs-ide-sdk
ms.topic: conceptual
helpviewer_keywords:
- command-line switches, adding
- command-line switches, retrieving
- IVsAppCommandLine::GetOption method
- command line, switches
ms.assetid: 8bbbd87e-76fe-4fb5-8ef9-65f5e31967cf
caps.latest.revision: 22
ms.author: gregvanl
manager: jillfra
ms.openlocfilehash: e28a3f303849458a407b212d3aad1a8c198f6d25
ms.sourcegitcommit: 6cfffa72af599a9d667249caaaa411bb28ea69fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2020
ms.locfileid: "62562270"
---
# <a name="adding-command-line-switches"></a>Adicionando opções de linha de comando
[!INCLUDE[vs2017banner](../includes/vs2017banner.md)]

Você pode adicionar opções de linha de comando que se aplicam ao seu VSPackage quando devenv.exe é executado. Use <xref:Microsoft.VisualStudio.Shell.ProvideAppCommandLineAttribute> para declarar o nome do comutador e suas propriedades. Neste exemplo, a opção mySwitch é adicionada a uma subclasse de VSPackage chamada **AddCommandSwitchPackage** sem argumentos e com o VSPackage carregado automaticamente.  
  
```csharp  
[ProvideAppCommandLine("MySwitch", typeof(AddCommandSwitchPackage), Arguments = "0", DemandLoad = 1)]  
```  
  
 Os parâmetros nomeados são mostrados na tabela a seguir  
  
 Argumentos  
 O número de argumentos para a opção. Pode ser "*" ou uma lista de argumentos.  
  
 À DEMANDLOAD  
 Carregue o VSPackage automaticamente se ele estiver definido como 1, caso contrário, definido como 0.  
  
 HelpString  
 A cadeia de caracteres de ajuda ou a ID de recurso da cadeia de caracteres a ser exibida com **devenv/?**.  
  
 Name  
 A opção.  
  
 PackageGuid  
 O GUID do pacote.  
  
 O primeiro valor de argumentos é geralmente 0 ou 1. Um valor especial de ' * ' pode ser usado para indicar que todo o restante da linha de comando é o argumento. Isso pode ser útil para cenários de depuração em que um usuário deve passar uma cadeia de comando de depurador.  
  
 O valor de À DEMANDLOAD é `true` (1) ou `false` (0) indica que o VSPackage deve ser carregado automaticamente.  
  
 O valor de HelpString é a ID de recurso da cadeia de caracteres que aparece no devenv/? Exibição da ajuda. Esse valor deve estar no formato "#nnn", em que NNN é um inteiro. O valor da cadeia de caracteres no arquivo de recurso deve terminar em um caractere de nova linha.  
  
 O nome valor é o nome da opção.  
  
 O valor de PackageGuid é o GUID do pacote que implementa essa opção. O IDE usa esse GUID para localizar o VSPackage no registro ao qual a opção de linha de comando se aplica.  
  
## <a name="retrieving-command-line-switches"></a>Recuperando opções de linha de comando  
 Quando o pacote for carregado, você poderá recuperar as opções de linha de comando concluindo as etapas a seguir.  
  
1. Na implementação do seu VSPackage <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A> , chame `QueryService` <xref:Microsoft.VisualStudio.Shell.Interop.SVsAppCommandLine> para obter a <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine> interface.  
  
2. Chame <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine.GetOption%2A> para recuperar as opções de linha de comando que o usuário inseriu.  
  
   O código a seguir mostra como descobrir se a opção de linha de comando mySwitch foi inserida pelo usuário:  
  
```csharp  
IVsAppCommandLine cmdline = (IVsAppCommandLine)GetService(typeof(SVsAppCommandLine));  
  
int isPresent = 0;  
string optionValue = "";  
  
cmdline.GetOption("MySwitch", out isPresent, out optionValue);  
```  
  
 É sua responsabilidade verificar se há opções de linha de comando sempre que seu pacote for carregado.  
  
## <a name="see-also"></a>Consulte Também  
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsAppCommandLine>   
 <xref:Microsoft.VisualStudio.Shell.Interop.IVsPackage.SetSite%2A>   
 [Opções de linha de comando do devenv](../ide/reference/devenv-command-line-switches.md)   
 [Utilitário CreatePkgDef](../extensibility/internals/createpkgdef-utility.md)   
 [Arquivos .Pkgdef](../extensibility/modifying-the-isolated-shell-by-using-the-dot-pkgdef-file.md)
