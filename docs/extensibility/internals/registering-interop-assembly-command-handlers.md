---
title: Registrando manipuladores de comando de montagem interop | Microsoft Docs
ms.date: 11/04/2016
ms.topic: conceptual
helpviewer_keywords:
- interop assemblies, command handlers
- command handling with interop assemblies, registering
ms.assetid: 303cd399-e29d-4ea1-8abe-5e0b59c12a0c
author: acangialosi
ms.author: anthc
manager: jillfra
ms.workload:
- vssdk
ms.openlocfilehash: 7e2ab6389f1e0d369dd095290d12c97431c44155
ms.sourcegitcommit: 16a4a5da4a4fd795b46a0869ca2152f2d36e6db2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/06/2020
ms.locfileid: "80705855"
---
# <a name="registering-interop-assembly-command-handlers"></a>Registrando manipuladores de comando de assembly de interoperabilidade
Um VSPackage deve [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] ser registrado para que o ambiente de desenvolvimento integrado (IDE) encaminhe seus comandos corretamente.

 O registro pode ser atualizado por edição manual ou usando um arquivo Registrador (.rgs). Para obter mais informações, consulte [Criando scripts de registrador](/cpp/atl/creating-registrar-scripts).

 O MPF (Managed Package Framework, quadro <xref:Microsoft.VisualStudio.Shell.ProvideMenuResourceAttribute> de pacotes gerenciados) fornece essa funcionalidade através da classe.

- [Os](https://msdn.microsoft.com/library/09e9c6ef-9863-48de-9483-d45b7b7c798f) recursos de referência do formato da tabela de comando estão localizados em dlls de ui de satélite não gerenciados.

## <a name="command-handler-registration-of-a-vspackage"></a>Registro do manipulador de comando de um vspackage
 Um VSPackage agindo como um manipulador para comandos baseados em interface de `GUID`usuário (UI) requer uma entrada de registro com o nome do VSPackage . Esta entrada de registro especifica a localização do arquivo de recursos de ida e rei do VSPackage e o recurso de menu dentro desse arquivo. A entrada de registro em si está localizada\\sob HKEY_LOCAL_MACHINE\Software\Microsoft\VisualStudio*\<Versão>* \Menus, onde [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] * \<a versão>* é a versão de , por exemplo, 9.0.

> [!NOTE]
> O caminho raiz do HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\VisualStudio\\*\<Versão>* pode ser [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)] substituído por uma raiz alternativa quando o shell é inicializado. Para obter mais informações sobre o caminho raiz, consulte [Instalar VSPackages com o Instalador do Windows](../../extensibility/internals/installing-vspackages-with-windows-installer.md).

### <a name="the-ctmenu-resource-registry-entry"></a>A entrada do registro de recursos do CTMENU
 A estrutura da entrada do registro é:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\<Version>\
  Menus\
    <GUID> = <Resource Information>
```

 \<*GUID*> `GUID` é o do VSPackage no formulário {XXXXXX-XXXX-XXXX-XXXX-XXX-XXXXXXXXX}.

 A>de Informações de Recursos consiste em três elementos separados por vírgulas. * \<* Estes elementos são, em ordem:

 \<*Caminho para> de DLL de recursos,* \<> *de id de recursos do menu,* \< *versão do menu*>

 A tabela a seguir \<descreve os campos de informações de *recursos*>.

| Elemento | Descrição |
|---------------------------| - |
| \<*Caminho para dll de recursos*> | Este é o caminho completo para o recurso DLL que contém o recurso do menu ou este é deixado em branco, indicando que o DLL de recurso do VSPackage deve ser usado (conforme especificado na subchave Pacotes onde o próprio VSPackage está registrado).<br /><br /> É costume deixar este campo em branco. |
| \<*ID do recurso do menu*> | Este é o ID `CTMENU` de recurso do recurso que contém todos os elementos de IU para o VSPackage compilados a partir de um arquivo [.vsct.](../../extensibility/internals/visual-studio-command-table-dot-vsct-files.md) |
| \<*Versão do menu*> | Este é um número usado `CTMENU` como uma versão para o recurso. [!INCLUDE[vsprvs](../../code-quality/includes/vsprvs_md.md)]usa esse valor para determinar se ele precisa `CTMENU` ressurgir o `CTMENU` conteúdo do recurso com seu cache de todos os recursos. Um remerge é acionado executando o comando de configuração devenv.<br /><br /> Este valor deve ser inicialmente definido como 1 `CTMENU` e incrementado após cada alteração no recurso e antes que o remerge ocorra. |

### <a name="example"></a>Exemplo
 Aqui está um exemplo de algumas entradas de recursos:

```
HKEY_LOCAL_MACHINE\Software\VisualStudio\9.0Exp\
  Menus\
    {019971D6-4685-11D2-B48A-0000F87572EB} = ,1, 10
    {1b027a40-8f43-11d0-8d11-00a0c91bc942} = , 10211, 3
```

## <a name="see-also"></a>Confira também
- [Como os VSPackages adicionam elementos da interface do usuário](../../extensibility/internals/how-vspackages-add-user-interface-elements.md)
- [Comandos e menus que usam assemblies de interoperabilidade](../../extensibility/internals/commands-and-menus-that-use-interop-assemblies.md)
