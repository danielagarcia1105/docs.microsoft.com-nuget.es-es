---
title: Formatos de analizador de .NET Compiler Platform para NuGet | Microsoft Docs
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 01/09/2017
ms.topic: article
ms.prod: nuget
ms.technology: 
description: Convenciones para los analizadores de .NET que se empaquetan y distribuyen con paquetes NuGet que implementan una API o biblioteca.
keywords: Convenciones de analizadores de NuGet, analizadores .NET, NuGet y .NET Compiler Platform, NuGet y Roslyn
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: e44cfa609c14422d50769e512108844cbd2f96a4
ms.sourcegitcommit: 24997b5345a997501fff846c9bd73610245ae0a6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/31/2018
---
# <a name="analyzer-nuget-formats"></a><span data-ttu-id="faf23-104">Formatos de analizadores de NuGet</span><span class="sxs-lookup"><span data-stu-id="faf23-104">Analyzer NuGet formats</span></span>

<span data-ttu-id="faf23-105">.NET Compiler Platform (también conocida como "Roslyn") permite a los desarrolladores crear [analizadores] (https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix) que examinan el árbol de sintaxis y la semántica del código mientras se escribe.</span><span class="sxs-lookup"><span data-stu-id="faf23-105">The .NET Compiler Platform (also known as "Roslyn") allow developers to create [analyzers] (https://github.com/dotnet/roslyn/wiki/How-To-Write-a-C%23-Analyzer-and-Code-Fix) that examine the syntax tree and semantics of code as it's being written.</span></span> <span data-ttu-id="faf23-106">Esto proporciona a los desarrolladores una manera de crear herramientas de análisis específicas del dominio, como las que podrían servir de ayuda para usar una API o biblioteca concreta.</span><span class="sxs-lookup"><span data-stu-id="faf23-106">This provides developers with a way to create and domain-specific analysis tools, such as those that would help guide the use of a particular API or library.</span></span> <span data-ttu-id="faf23-107">Puede encontrar más información en la wiki de GitHub [.NET/Roslyn](https://github.com/dotnet/roslyn/wiki).</span><span class="sxs-lookup"><span data-stu-id="faf23-107">You can find more information on the [.NET/Roslyn](https://github.com/dotnet/roslyn/wiki) GitHub wiki.</span></span> <span data-ttu-id="faf23-108">Vea también el artículo [Use Roslyn to Write a Live Code Analyzer for your API](https://msdn.microsoft.com/magazine/dn879356.aspx) (Usar Roslyn para escribir un analizador de código dinámico para la API) en MSDN Magazine.</span><span class="sxs-lookup"><span data-stu-id="faf23-108">Also see the article, [Use Roslyn to Write a Live Code Analyzer for your API](https://msdn.microsoft.com/magazine/dn879356.aspx) in MSDN Magazine.</span></span>

<span data-ttu-id="faf23-109">Los propios analizadores normalmente se empaquetan y distribuyen como parte de los paquetes NuGet que implementan la biblioteca o API en cuestión.</span><span class="sxs-lookup"><span data-stu-id="faf23-109">Analyzers themselves are typically packaged and distributed as part of the NuGet packages that implement the API or library in question.</span></span>

<span data-ttu-id="faf23-110">Para obtener un buen ejemplo, vea el paquete [System.Runtime.Analyzers](https://www.nuget.org/packages/System.Runtime.Analyzers), que tiene el contenido siguiente:</span><span class="sxs-lookup"><span data-stu-id="faf23-110">For a good example, see the [System.Runtime.Analyzers](https://www.nuget.org/packages/System.Runtime.Analyzers) package, which has the following contents:</span></span>

- <span data-ttu-id="faf23-111">analyzers\dotnet\System.Runtime.Analyzers.dll</span><span class="sxs-lookup"><span data-stu-id="faf23-111">analyzers\dotnet\System.Runtime.Analyzers.dll</span></span>
- <span data-ttu-id="faf23-112">analyzers\dotnet\cs\System.Runtime.CSharp.Analyzers.dll</span><span class="sxs-lookup"><span data-stu-id="faf23-112">analyzers\dotnet\cs\System.Runtime.CSharp.Analyzers.dll</span></span>
- <span data-ttu-id="faf23-113">analyzers\dotnet\vb\System.Runtime.VisualBasic.Analyzers.dll</span><span class="sxs-lookup"><span data-stu-id="faf23-113">analyzers\dotnet\vb\System.Runtime.VisualBasic.Analyzers.dll</span></span>
- <span data-ttu-id="faf23-114">build\System.Runtime.Analyzers.Common.props</span><span class="sxs-lookup"><span data-stu-id="faf23-114">build\System.Runtime.Analyzers.Common.props</span></span>
- <span data-ttu-id="faf23-115">build\System.Runtime.Analyzers.props</span><span class="sxs-lookup"><span data-stu-id="faf23-115">build\System.Runtime.Analyzers.props</span></span>
- <span data-ttu-id="faf23-116">build\System.Runtime.CSharp.Analyzers.props</span><span class="sxs-lookup"><span data-stu-id="faf23-116">build\System.Runtime.CSharp.Analyzers.props</span></span>
- <span data-ttu-id="faf23-117">build\System.Runtime.VisualBasic.Analyzers.props</span><span class="sxs-lookup"><span data-stu-id="faf23-117">build\System.Runtime.VisualBasic.Analyzers.props</span></span>
- <span data-ttu-id="faf23-118">tools\install.ps1</span><span class="sxs-lookup"><span data-stu-id="faf23-118">tools\install.ps1</span></span>
- <span data-ttu-id="faf23-119">tools\uninstall.ps1</span><span class="sxs-lookup"><span data-stu-id="faf23-119">tools\uninstall.ps1</span></span>

<span data-ttu-id="faf23-120">Como puede ver, los archivos DLL del analizador se colocan en una carpeta `analyzers` en el paquete.</span><span class="sxs-lookup"><span data-stu-id="faf23-120">As you can see, you place the analyzer DLLs into an `analyzers` folder in the package.</span></span>

<span data-ttu-id="faf23-121">Los archivos de propiedades, que se incluyen para deshabilitar reglas heredadas de FxCop en favor de la implementación del analizador, se colocan en la carpeta `build`.</span><span class="sxs-lookup"><span data-stu-id="faf23-121">Props files, which are included to disable legacy FxCop rules in favor of the analyzer implementation, are placed in the `build` folder.</span></span>

<span data-ttu-id="faf23-122">Los scripts de instalación y desinstalación que admiten proyectos en los que se usa `packages.config` se colocan en `tools`.</span><span class="sxs-lookup"><span data-stu-id="faf23-122">Install and uninstall scripts that support projects using `packages.config` are placed in `tools`.</span></span>

<span data-ttu-id="faf23-123">También tenga en cuenta que, como este paquete no tiene ningún requisito específico de la plataforma, la carpeta `platform` se omite.</span><span class="sxs-lookup"><span data-stu-id="faf23-123">Also note that because this package has no platform-specific requirements, the `platform` folder is omitted.</span></span>


## <a name="analyzers-path-format"></a><span data-ttu-id="faf23-124">Formato de ruta de acceso de analizadores</span><span class="sxs-lookup"><span data-stu-id="faf23-124">Analyzers path format</span></span>

<span data-ttu-id="faf23-125">El uso de la carpeta `analyzers` es similar a la que se usa para [plataformas de destino](../create-packages/supporting-multiple-target-frameworks.md), salvo que los especificadores en la ruta de acceso describen las dependencias del host de desarrollo en lugar del de tiempo de compilación.</span><span class="sxs-lookup"><span data-stu-id="faf23-125">The use of the `analyzers` folder is similar to that used for [target frameworks](../create-packages/supporting-multiple-target-frameworks.md), except the specifiers in the path describe development host dependencies instead of build-time.</span></span> <span data-ttu-id="faf23-126">El formato general es el siguiente:</span><span class="sxs-lookup"><span data-stu-id="faf23-126">The general format is as follows:</span></span>

    $/analyzers/{framework_name}{version}/{supported_architecture}/{supported_language}}/{analyzer_name}.dll

- <span data-ttu-id="faf23-127">**nombre_plataforma**: el área expuesta de API *opcional* de .NET Framework que deben ejecutar los archivos DLL incluidos.</span><span class="sxs-lookup"><span data-stu-id="faf23-127">**framework_name**: the *optional* API surface area of the .NET Framework that the contained DLLs need to run.</span></span> <span data-ttu-id="faf23-128">`dotnet` es actualmente el único valor válido porque Roslyn es el único host que puede ejecutar analizadores.</span><span class="sxs-lookup"><span data-stu-id="faf23-128">`dotnet` is presently the only valid value because Roslyn is the only host that can run analyzers.</span></span> <span data-ttu-id="faf23-129">Si no se especifica ningún destino, se supone que los archivos DLL se aplican a *todos* los destinos.</span><span class="sxs-lookup"><span data-stu-id="faf23-129">If no target is specified, DLLs are assumed to apply to *all* targets.</span></span>
- <span data-ttu-id="faf23-130">**lenguaje_admitido**: el lenguaje para el que se aplica el archivo DLL, uno de entre `cs` (C#), `vb` (Visual Basic) y `fs` (F#).</span><span class="sxs-lookup"><span data-stu-id="faf23-130">**supported_language**: the language for which the DLL applies, one of `cs` (C#) and `vb` (Visual Basic), and `fs` (F#).</span></span> <span data-ttu-id="faf23-131">El lenguaje indica que el analizador se debe cargar solo para un proyecto en el que se use ese lenguaje.</span><span class="sxs-lookup"><span data-stu-id="faf23-131">The language indicates that the analyzer should be loaded only for a project using that language.</span></span> <span data-ttu-id="faf23-132">Si no se especifica ningún lenguaje, se supone que el archivo DLL se aplica a *todos* los lenguajes que admitan analizadores.</span><span class="sxs-lookup"><span data-stu-id="faf23-132">If no language is specified then DLL is assumed to apply to *all* languages that support analyzers.</span></span>
- <span data-ttu-id="faf23-133">**nombre_analizador**: especifica los archivos DLL del analizador.</span><span class="sxs-lookup"><span data-stu-id="faf23-133">**analyzer_name**: specifies the DLLs of the analyzer.</span></span> <span data-ttu-id="faf23-134">Si se necesitan archivos adicionales además de los archivos DLL, se deben incluir a través de archivos de destinos o propiedades.</span><span class="sxs-lookup"><span data-stu-id="faf23-134">If you need additional files beyond DLLs, they must be included through a targets or properties files.</span></span>


## <a name="install-and-uninstall-scripts"></a><span data-ttu-id="faf23-135">Scripts de instalación y desinstalación</span><span class="sxs-lookup"><span data-stu-id="faf23-135">Install and uninstall scripts</span></span>

<span data-ttu-id="faf23-136">Si en el proyecto del usuario se usa `packages.config`, el script de MSBuild que elige el analizador no interviene, por lo que se deben incluir `install.ps1` y `uninstall.ps1` en la carpeta `tools` con el contenido que se describe a continuación.</span><span class="sxs-lookup"><span data-stu-id="faf23-136">If the user's project is using `packages.config`, the MSBuild script that picks up the analyzer does not come into play, so you should `install.ps1` and `uninstall.ps1` in the `tools` folder with the contents that are described below.</span></span>

<span data-ttu-id="faf23-137">**Contenido del archivo install.ps1**</span><span class="sxs-lookup"><span data-stu-id="faf23-137">**install.ps1 file contents**</span></span>

```ps
param($installPath, $toolsPath, $package, $project)

$analyzersPaths = Join-Path (Join-Path (Split-Path -Path $toolsPath -Parent) "analyzers" ) * -Resolve

foreach($analyzersPath in $analyzersPaths)
{
    # Install the language agnostic analyzers.
    if (Test-Path $analyzersPath)
    {
        foreach ($analyzerFilePath in Get-ChildItem $analyzersPath -Filter *.dll)
        {
            if($project.Object.AnalyzerReferences)
            {
                $project.Object.AnalyzerReferences.Add($analyzerFilePath.FullName)
            }
        }
    }
}

$project.Type # gives the language name like (C# or VB.NET)
$languageFolder = ""
if($project.Type -eq "C#")
{
    $languageFolder = "cs"
}
if($project.Type -eq "VB.NET")
{
    $languageFolder = "vb"
}
if($languageFolder -eq "")
{
    return
}

foreach($analyzersPath in $analyzersPaths)
{
    # Install language specific analyzers.
    $languageAnalyzersPath = join-path $analyzersPath $languageFolder
    if (Test-Path $languageAnalyzersPath)
    {
        foreach ($analyzerFilePath in Get-ChildItem $languageAnalyzersPath -Filter *.dll)
        {
            if($project.Object.AnalyzerReferences)
            {
                $project.Object.AnalyzerReferences.Add($analyzerFilePath.FullName)
            }
        }
    }
}
```


<span data-ttu-id="faf23-138">**Contenido del archivo uninstall.ps1**</span><span class="sxs-lookup"><span data-stu-id="faf23-138">**uninstall.ps1 file contents**</span></span>

```ps
param($installPath, $toolsPath, $package, $project)

$analyzersPaths = Join-Path (Join-Path (Split-Path -Path $toolsPath -Parent) "analyzers" ) * -Resolve

foreach($analyzersPath in $analyzersPaths)
{
    # Uninstall the language agnostic analyzers.
    if (Test-Path $analyzersPath)
    {
        foreach ($analyzerFilePath in Get-ChildItem $analyzersPath -Filter *.dll)
        {
            if($project.Object.AnalyzerReferences)
            {
                $project.Object.AnalyzerReferences.Remove($analyzerFilePath.FullName)
            }
        }
    }
}

$project.Type # gives the language name like (C# or VB.NET)
$languageFolder = ""
if($project.Type -eq "C#")
{
    $languageFolder = "cs"
}
if($project.Type -eq "VB.NET")
{
    $languageFolder = "vb"
}
if($languageFolder -eq "")
{
    return
}

foreach($analyzersPath in $analyzersPaths)
{
    # Uninstall language specific analyzers.
    $languageAnalyzersPath = join-path $analyzersPath $languageFolder
    if (Test-Path $languageAnalyzersPath)
    {
        foreach ($analyzerFilePath in Get-ChildItem $languageAnalyzersPath -Filter *.dll)
        {
            if($project.Object.AnalyzerReferences)
            {
                try
                {
                    $project.Object.AnalyzerReferences.Remove($analyzerFilePath.FullName)
                }
                catch
                {

                }
            }
        }
    }
}
```