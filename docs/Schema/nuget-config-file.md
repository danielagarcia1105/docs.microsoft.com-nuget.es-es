---
title: Referencia del archivo NuGet.Config | Microsoft Docs
author: kraigb
ms.author: kraigb
manager: ghogen
ms.date: 10/25/2017
ms.topic: reference
ms.prod: nuget
ms.technology: 
ms.assetid: fbf31530-3bf4-478c-b26c-c2b24dd3406d
description: Referencia del archivo NuGet.Config en la que se incluyen las secciones config, bindingRedirects, packageRestore, solution y packageSource.
keywords: "Archivo NuGet.Config, referencia de configuración de NuGet, opciones de configuración de NuGet"
ms.reviewer:
- karann-msft
- unniravindranathan
ms.openlocfilehash: 830c622f622b894a228b18dfdb3a790bccfde8a3
ms.sourcegitcommit: bdcd2046b1b187d8b59716b9571142c02181c8fb
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/10/2018
---
# <a name="nugetconfig-reference"></a><span data-ttu-id="d7b18-104">Referencia de NuGet.Config</span><span class="sxs-lookup"><span data-stu-id="d7b18-104">NuGet.Config reference</span></span>

<span data-ttu-id="d7b18-105">El comportamiento de NuGet se controla mediante la configuración en diferentes archivos `NuGet.Config`, como se describe en [Configuración del comportamiento de NuGet](../consume-packages/configuring-nuget-behavior.md).</span><span class="sxs-lookup"><span data-stu-id="d7b18-105">NuGet behavior is controlled by settings in different `NuGet.Config` files as described in [Configuring NuGet Behavior](../consume-packages/configuring-nuget-behavior.md).</span></span>

<span data-ttu-id="d7b18-106">`NuGet.Config` es un archivo XML que contiene un nodo `<configuration>` de nivel superior, que contiene los elementos de sección que se describen en este tema.</span><span class="sxs-lookup"><span data-stu-id="d7b18-106">`NuGet.Config` is an XML file containing a top-level `<configuration>` node, which then contains the section elements described in this topic.</span></span> <span data-ttu-id="d7b18-107">Cada sección contiene cero o más elementos `<add>` con atributos `key` y `value`.</span><span class="sxs-lookup"><span data-stu-id="d7b18-107">Each section contains zero or more `<add>` elements with `key` and `value` attributes.</span></span> <span data-ttu-id="d7b18-108">Vea el [archivo de configuración de ejemplo](#example-config-file).</span><span class="sxs-lookup"><span data-stu-id="d7b18-108">See the [examples config file](#example-config-file).</span></span> <span data-ttu-id="d7b18-109">Los nombres de opción distinguen mayúsculas de minúsculas, y los valores pueden usar [variables de entorno](#using-environment-variables).</span><span class="sxs-lookup"><span data-stu-id="d7b18-109">Setting names are case-insensitive, and values can use [environment variables](#using-environment-variables).</span></span>

<span data-ttu-id="d7b18-110">En este tema:</span><span class="sxs-lookup"><span data-stu-id="d7b18-110">In this topic:</span></span>

- [<span data-ttu-id="d7b18-111">Sección config</span><span class="sxs-lookup"><span data-stu-id="d7b18-111">config section</span></span>](#config-section)
- [<span data-ttu-id="d7b18-112">Sección bindingRedirects</span><span class="sxs-lookup"><span data-stu-id="d7b18-112">bindingRedirects section</span></span>](#bindingredirects-section)
- [<span data-ttu-id="d7b18-113">Sección packageRestore</span><span class="sxs-lookup"><span data-stu-id="d7b18-113">packageRestore section</span></span>](#packagerestore-section)
- [<span data-ttu-id="d7b18-114">Sección solution</span><span class="sxs-lookup"><span data-stu-id="d7b18-114">solution section</span></span>](#solution-section)
- <span data-ttu-id="d7b18-115">[Secciones de origen del paquete](#package-source-sections): -[packageSources](#packagesources)</span><span class="sxs-lookup"><span data-stu-id="d7b18-115">[Package source sections](#package-source-sections): -[packageSources](#packagesources)</span></span>
  - [<span data-ttu-id="d7b18-116">packageSourceCredentials</span><span class="sxs-lookup"><span data-stu-id="d7b18-116">packageSourceCredentials</span></span>](#packagesourcecredentials)
  - [<span data-ttu-id="d7b18-117">apikeys</span><span class="sxs-lookup"><span data-stu-id="d7b18-117">apikeys</span></span>](#apikeys)
  - [<span data-ttu-id="d7b18-118">disabledPackageSources</span><span class="sxs-lookup"><span data-stu-id="d7b18-118">disabledPackageSources</span></span>](#disabledpackagesources)
  - [<span data-ttu-id="d7b18-119">activePackageSource</span><span class="sxs-lookup"><span data-stu-id="d7b18-119">activePackageSource</span></span>](#activepackagesource)
- [<span data-ttu-id="d7b18-120">Uso de variables de entorno</span><span class="sxs-lookup"><span data-stu-id="d7b18-120">Using environment variables</span></span>](#using-environment-variables)
- [<span data-ttu-id="d7b18-121">Archivo de configuración de ejemplo</span><span class="sxs-lookup"><span data-stu-id="d7b18-121">Example config file</span></span>](#example-config-file)

<a name="dependencyVersion"></a>
<a name="globalPackagesFolder"></a>
<a name="repositoryPath"></a>
<a name="proxy-settings"></a>

## <a name="config-section"></a><span data-ttu-id="d7b18-122">Sección config</span><span class="sxs-lookup"><span data-stu-id="d7b18-122">config section</span></span>

<span data-ttu-id="d7b18-123">Contiene varios valores de configuración, que se pueden establecer mediante el [comando `nuget config`](../tools/cli-ref-config.md).</span><span class="sxs-lookup"><span data-stu-id="d7b18-123">Contains miscellaneous configuration settings, which can be set using the [`nuget config` command](../tools/cli-ref-config.md).</span></span>

<span data-ttu-id="d7b18-124">Nota: `dependencyVersion` y `repositoryPath` solo se aplican a proyectos en los que se usa `packages.config`.</span><span class="sxs-lookup"><span data-stu-id="d7b18-124">Note: `dependencyVersion` and `repositoryPath` apply only to projects using `packages.config`.</span></span> <span data-ttu-id="d7b18-125">`globalPackagesFolder` solo se aplica a proyectos en los que se usa `project.json` y formatos de PackageReference.</span><span class="sxs-lookup"><span data-stu-id="d7b18-125">`globalPackagesFolder` applies only to projects using `project.json` and PackageReference formats.</span></span>

| <span data-ttu-id="d7b18-126">Key</span><span class="sxs-lookup"><span data-stu-id="d7b18-126">Key</span></span> | <span data-ttu-id="d7b18-127">Valor</span><span class="sxs-lookup"><span data-stu-id="d7b18-127">Value</span></span> |
| --- | --- |
| <span data-ttu-id="d7b18-128">dependencyVersion (solo `packages.config`)</span><span class="sxs-lookup"><span data-stu-id="d7b18-128">dependencyVersion (`packages.config` only)</span></span> | <span data-ttu-id="d7b18-129">El valor predeterminado `DependencyVersion` para la instalación, restauración y actualización del paquete, cuando no se especifica directamente el modificador `-DependencyVersion`.</span><span class="sxs-lookup"><span data-stu-id="d7b18-129">The default `DependencyVersion` value for package install, restore, and update, when the `-DependencyVersion` switch is not specified directly.</span></span> <span data-ttu-id="d7b18-130">Este valor también se usa en la interfaz de usuario del Administrador de paquetes NuGet.</span><span class="sxs-lookup"><span data-stu-id="d7b18-130">This value is also used by the NuGet Package Manager UI.</span></span> <span data-ttu-id="d7b18-131">Los valores son `Lowest`, `HighestPatch`, `HighestMinor`, `Highest`.</span><span class="sxs-lookup"><span data-stu-id="d7b18-131">Values are `Lowest`, `HighestPatch`, `HighestMinor`, `Highest`.</span></span> |
| <span data-ttu-id="d7b18-132">globalPackagesFolder (proyectos en los que no se usa `packages.config`)</span><span class="sxs-lookup"><span data-stu-id="d7b18-132">globalPackagesFolder (projects not using `packages.config`)</span></span> | <span data-ttu-id="d7b18-133">La ubicación de la carpeta de paquetes global predeterminada.</span><span class="sxs-lookup"><span data-stu-id="d7b18-133">The location of the default global packages folder.</span></span> <span data-ttu-id="d7b18-134">El valor predeterminado es `%USERPROFILE%\.nuget\packages` (Windows) o `~/.nuget/packages` (Mac o Linux).</span><span class="sxs-lookup"><span data-stu-id="d7b18-134">The default is `%USERPROFILE%\.nuget\packages` (Windows) or `~/.nuget/packages` (Mac/Linux).</span></span> <span data-ttu-id="d7b18-135">Se puede usar una ruta de acceso relativa en archivos `Nuget.Config` específicos del proyecto.</span><span class="sxs-lookup"><span data-stu-id="d7b18-135">A relative path can be used in project-specific `Nuget.Config` files.</span></span> |
| <span data-ttu-id="d7b18-136">repositoryPath (solo `packages.config`)</span><span class="sxs-lookup"><span data-stu-id="d7b18-136">repositoryPath (`packages.config` only)</span></span> | <span data-ttu-id="d7b18-137">La ubicación en la que se van a instalar los paquetes NuGet en lugar de la carpeta `$(Solutiondir)/packages` predeterminada.</span><span class="sxs-lookup"><span data-stu-id="d7b18-137">The location in which to install NuGet packages instead of the default `$(Solutiondir)/packages` folder.</span></span> <span data-ttu-id="d7b18-138">Se puede usar una ruta de acceso relativa en archivos `Nuget.Config` específicos del proyecto.</span><span class="sxs-lookup"><span data-stu-id="d7b18-138">A relative path can be used in project-specific `Nuget.Config` files.</span></span> |
| <span data-ttu-id="d7b18-139">defaultPushSource</span><span class="sxs-lookup"><span data-stu-id="d7b18-139">defaultPushSource</span></span> | <span data-ttu-id="d7b18-140">Identifica la dirección URL o ruta de acceso de origen del paquete que se debe usar como valor predeterminado si no se encuentra ningún otro origen del paquete para una operación.</span><span class="sxs-lookup"><span data-stu-id="d7b18-140">Identifies the URL or path of the package source that should be used as the default if no other package sources are found for an operation.</span></span> |
| <span data-ttu-id="d7b18-141">http_proxy http_proxy.user http_proxy.password no_proxy</span><span class="sxs-lookup"><span data-stu-id="d7b18-141">http_proxy http_proxy.user http_proxy.password no_proxy</span></span> | <span data-ttu-id="d7b18-142">Configuración de proxy que se usa al conectarse a orígenes de paquetes; `http_proxy` debe tener el formato `http://<username>:<password>@<domain>`.</span><span class="sxs-lookup"><span data-stu-id="d7b18-142">Proxy settings to use when connecting to package sources; `http_proxy` should be in the format `http://<username>:<password>@<domain>`.</span></span> <span data-ttu-id="d7b18-143">Las contraseñas están cifradas y no se pueden agregar de forma manual.</span><span class="sxs-lookup"><span data-stu-id="d7b18-143">Passwords are encrypted and cannot be added manually.</span></span> <span data-ttu-id="d7b18-144">Para `no_proxy`, el valor es una lista separada por comas de dominios que omiten el servidor proxy.</span><span class="sxs-lookup"><span data-stu-id="d7b18-144">For `no_proxy`, the value is a comma-separated list of domains the bypass the proxy server.</span></span> <span data-ttu-id="d7b18-145">Como alternativa, puede usar las variables de entorno http_proxy y no_proxy para esos valores.</span><span class="sxs-lookup"><span data-stu-id="d7b18-145">You can alternately use the http_proxy and no_proxy environment variables for those values.</span></span> <span data-ttu-id="d7b18-146">Para obtener más información, vea [Configuración de proxy de NuGet](http://skolima.blogspot.com/2012/07/nuget-proxy-settings.html) (skolima.blogspot.com).</span><span class="sxs-lookup"><span data-stu-id="d7b18-146">For additional details, see [NuGet proxy settings](http://skolima.blogspot.com/2012/07/nuget-proxy-settings.html) (skolima.blogspot.com).</span></span> |

<span data-ttu-id="d7b18-147">**Ejemplo**:</span><span class="sxs-lookup"><span data-stu-id="d7b18-147">**Example**:</span></span>

```xml
<config>
    <add key="dependencyVersion" value="Highest" />
    <add key="globalPackagesFolder" value="c:\packages" />
    <add key="repositoryPath" value="c:\repo" />
    <add key="http_proxy" value="http://company-squid:3128@contoso.com" />
</config>
```

## <a name="bindingredirects-section"></a><span data-ttu-id="d7b18-148">Sección bindingRedirects</span><span class="sxs-lookup"><span data-stu-id="d7b18-148">bindingRedirects section</span></span>

<span data-ttu-id="d7b18-149">Configura si NuGet realiza redirecciones de enlaces automáticas cuando se instala un paquete.</span><span class="sxs-lookup"><span data-stu-id="d7b18-149">Configures whether NuGet does automatic binding redirects when a package is installed.</span></span>

| <span data-ttu-id="d7b18-150">Key</span><span class="sxs-lookup"><span data-stu-id="d7b18-150">Key</span></span> | <span data-ttu-id="d7b18-151">Valor</span><span class="sxs-lookup"><span data-stu-id="d7b18-151">Value</span></span> |
| --- | --- |
| <span data-ttu-id="d7b18-152">skip</span><span class="sxs-lookup"><span data-stu-id="d7b18-152">skip</span></span> | <span data-ttu-id="d7b18-153">Un valor booleano que indica si se omiten las redirecciones de enlaces automáticas.</span><span class="sxs-lookup"><span data-stu-id="d7b18-153">A Boolean indicating whether to skip automatic binding redirects.</span></span> <span data-ttu-id="d7b18-154">El valor predeterminado es false.</span><span class="sxs-lookup"><span data-stu-id="d7b18-154">The default is false.</span></span> |

<span data-ttu-id="d7b18-155">**Ejemplo**:</span><span class="sxs-lookup"><span data-stu-id="d7b18-155">**Example**:</span></span>

```xml
<bindingRedirects>
    <add key="skip" value="True" />
</bindingRedirects>
```

## <a name="packagerestore-section"></a><span data-ttu-id="d7b18-156">Sección packageRestore</span><span class="sxs-lookup"><span data-stu-id="d7b18-156">packageRestore section</span></span>

<span data-ttu-id="d7b18-157">*Se ignora en 2.7 y versiones posteriores*</span><span class="sxs-lookup"><span data-stu-id="d7b18-157">*Ignored in 2.7+*</span></span>

<span data-ttu-id="d7b18-158">Controla la restauración del paquete durante las compilaciones.</span><span class="sxs-lookup"><span data-stu-id="d7b18-158">Controls package restore during builds.</span></span>

| <span data-ttu-id="d7b18-159">Key</span><span class="sxs-lookup"><span data-stu-id="d7b18-159">Key</span></span> | <span data-ttu-id="d7b18-160">Valor</span><span class="sxs-lookup"><span data-stu-id="d7b18-160">Value</span></span> |
| --- | --- |
| <span data-ttu-id="d7b18-161">enabled</span><span class="sxs-lookup"><span data-stu-id="d7b18-161">enabled</span></span> | <span data-ttu-id="d7b18-162">Un valor booleano que indica si NuGet puede realizar la restauración automática.</span><span class="sxs-lookup"><span data-stu-id="d7b18-162">A Boolean indicating whether NuGet can perform automatic restore.</span></span> <span data-ttu-id="d7b18-163">También se puede establecer la variable de entorno `EnableNuGetPackageRestore` con un valor de `True` en lugar de establecer esta clave en el archivo de configuración.</span><span class="sxs-lookup"><span data-stu-id="d7b18-163">You can also set the `EnableNuGetPackageRestore` environment variable with a value of `True` instead of setting this key in the config file.</span></span> |
| <span data-ttu-id="d7b18-164">automáticamente</span><span class="sxs-lookup"><span data-stu-id="d7b18-164">automatic</span></span> | <span data-ttu-id="d7b18-165">Un valor booleano que indica si NuGet debe comprobar los paquetes que faltan durante una compilación.</span><span class="sxs-lookup"><span data-stu-id="d7b18-165">A Boolean indicating whether NuGet should check for missing packages during a build.</span></span> |

<span data-ttu-id="d7b18-166">**Ejemplo**:</span><span class="sxs-lookup"><span data-stu-id="d7b18-166">**Example**:</span></span>

```xml
<packageRestore>
    <add key="enabled" value="true" />
    <add key="automatic" value="true" />
</packageRestore>
```

## <a name="solution-section"></a><span data-ttu-id="d7b18-167">Sección solution</span><span class="sxs-lookup"><span data-stu-id="d7b18-167">solution section</span></span>

<span data-ttu-id="d7b18-168">Controla si la carpeta `packages` de una solución se incluye en el control de código fuente.</span><span class="sxs-lookup"><span data-stu-id="d7b18-168">Controls whether the `packages` folder of a solution is included in source control.</span></span> <span data-ttu-id="d7b18-169">En esta sección solo funciona en los archivos `Nuget.Config` de la carpeta de una solución.</span><span class="sxs-lookup"><span data-stu-id="d7b18-169">This section works only in `Nuget.Config` files in a solution folder.</span></span>

| <span data-ttu-id="d7b18-170">Key</span><span class="sxs-lookup"><span data-stu-id="d7b18-170">Key</span></span> | <span data-ttu-id="d7b18-171">Valor</span><span class="sxs-lookup"><span data-stu-id="d7b18-171">Value</span></span> |
| --- | --- |
| <span data-ttu-id="d7b18-172">disableSourceControlIntegration</span><span class="sxs-lookup"><span data-stu-id="d7b18-172">disableSourceControlIntegration</span></span> | <span data-ttu-id="d7b18-173">Un valor booleano que indica si se debe ignorar la carpeta de paquetes cuando se trabaja con el control de código fuente.</span><span class="sxs-lookup"><span data-stu-id="d7b18-173">A Boolean indicating whether to ignore the packages folder when working with source control.</span></span> <span data-ttu-id="d7b18-174">El valor predeterminado es false.</span><span class="sxs-lookup"><span data-stu-id="d7b18-174">The default value is false.</span></span> |

<span data-ttu-id="d7b18-175">**Ejemplo**:</span><span class="sxs-lookup"><span data-stu-id="d7b18-175">**Example**:</span></span>

```xml
<solution>
    <add key="disableSourceControlIntegration" value="true" />
</solution>
```

## <a name="package-source-sections"></a><span data-ttu-id="d7b18-176">Secciones de origen del paquete</span><span class="sxs-lookup"><span data-stu-id="d7b18-176">Package source sections</span></span>

<span data-ttu-id="d7b18-177">`packageSources`, `packageSourceCredentials`, `apikeys`, `activePackageSource` y `disabledPackageSources` trabajan de manera conjunta para configurar el funcionamiento de NuGet con repositorios de paquetes durante las operaciones de instalación, restauración y actualización.</span><span class="sxs-lookup"><span data-stu-id="d7b18-177">The `packageSources`, `packageSourceCredentials`, `apikeys`, `activePackageSource`, and `disabledPackageSources` all work together to configure how NuGet works with package repositories during install, restore, and update operations.</span></span>

<span data-ttu-id="d7b18-178">Normalmente se usa el [comando `nuget sources`](../tools/cli-ref-sources.md) para administrar estos valores, excepto para `apikeys` que se administra con el [comando `nuget setapikey`](../tools/cli-ref-setapikey.md).</span><span class="sxs-lookup"><span data-stu-id="d7b18-178">The [`nuget sources` command](../tools/cli-ref-sources.md) is generally used to manage these settings, except for `apikeys` which is managed using the [`nuget setapikey` command](../tools/cli-ref-setapikey.md).</span></span>

<span data-ttu-id="d7b18-179">Tenga en cuenta que la dirección URL de origen de nuget.org es `https://api.nuget.org/v3/index.json`.</span><span class="sxs-lookup"><span data-stu-id="d7b18-179">Note that the source URL for nuget.org is `https://api.nuget.org/v3/index.json`.</span></span>

### <a name="packagesources"></a><span data-ttu-id="d7b18-180">packageSources</span><span class="sxs-lookup"><span data-stu-id="d7b18-180">packageSources</span></span>

<span data-ttu-id="d7b18-181">Enumera todos los orígenes de paquetes conocidos.</span><span class="sxs-lookup"><span data-stu-id="d7b18-181">Lists all known package sources.</span></span>

| <span data-ttu-id="d7b18-182">Key</span><span class="sxs-lookup"><span data-stu-id="d7b18-182">Key</span></span> | <span data-ttu-id="d7b18-183">Valor</span><span class="sxs-lookup"><span data-stu-id="d7b18-183">Value</span></span> |
| --- | --- |
| <span data-ttu-id="d7b18-184">(nombre para asignar al origen del paquete)</span><span class="sxs-lookup"><span data-stu-id="d7b18-184">(name to assign to the package source)</span></span> | <span data-ttu-id="d7b18-185">La ruta de acceso o dirección URL del origen del paquete.</span><span class="sxs-lookup"><span data-stu-id="d7b18-185">The path or URL of the package source.</span></span> |

<span data-ttu-id="d7b18-186">**Ejemplo**:</span><span class="sxs-lookup"><span data-stu-id="d7b18-186">**Example**:</span></span>

```xml
<packageSources>
    <add key="nuget.org" value="https://api.nuget.org/v3/index.json" protocolVersion="3" />
    <add key="Contoso" value="https://contoso.com/packages/" />
    <add key="Test Source" value="c:\packages" />
</packageSources>
```

### <a name="packagesourcecredentials"></a><span data-ttu-id="d7b18-187">packageSourceCredentials</span><span class="sxs-lookup"><span data-stu-id="d7b18-187">packageSourceCredentials</span></span>

<span data-ttu-id="d7b18-188">Almacena nombres de usuario y contraseñas para los orígenes, normalmente especificados con los modificadores `-username` y `-password` con `nuget sources`.</span><span class="sxs-lookup"><span data-stu-id="d7b18-188">Stores usernames and passwords for sources, typically specified with the `-username` and `-password` switches with `nuget sources`.</span></span> <span data-ttu-id="d7b18-189">Las contraseñas se cifran de forma predeterminada a menos que también se use la opción `-storepasswordincleartext`.</span><span class="sxs-lookup"><span data-stu-id="d7b18-189">Passwords are encrypted by default unless the `-storepasswordincleartext` option is also used.</span></span>

| <span data-ttu-id="d7b18-190">Key</span><span class="sxs-lookup"><span data-stu-id="d7b18-190">Key</span></span> | <span data-ttu-id="d7b18-191">Valor</span><span class="sxs-lookup"><span data-stu-id="d7b18-191">Value</span></span> |
| --- | --- |
| <span data-ttu-id="d7b18-192">username</span><span class="sxs-lookup"><span data-stu-id="d7b18-192">username</span></span> | <span data-ttu-id="d7b18-193">El nombre de usuario para el origen en texto sin formato.</span><span class="sxs-lookup"><span data-stu-id="d7b18-193">The user name for the source in plain text.</span></span> |
| <span data-ttu-id="d7b18-194">contraseña</span><span class="sxs-lookup"><span data-stu-id="d7b18-194">password</span></span> | <span data-ttu-id="d7b18-195">La contraseña cifrada para el origen.</span><span class="sxs-lookup"><span data-stu-id="d7b18-195">The encrypted password for the source.</span></span> |
| <span data-ttu-id="d7b18-196">cleartextpassword</span><span class="sxs-lookup"><span data-stu-id="d7b18-196">cleartextpassword</span></span> | <span data-ttu-id="d7b18-197">La contraseña no cifrada para el origen.</span><span class="sxs-lookup"><span data-stu-id="d7b18-197">The unencrypted password for the source.</span></span> |

<span data-ttu-id="d7b18-198">**Ejemplo:**</span><span class="sxs-lookup"><span data-stu-id="d7b18-198">**Example:**</span></span>

<span data-ttu-id="d7b18-199">En el archivo de configuración, el elemento `<packageSourceCredentials>` contiene nodos secundarios para cada nombre de origen aplicable (los espacios en el nombre se reemplazan por `_x0020+`).</span><span class="sxs-lookup"><span data-stu-id="d7b18-199">In the config file, the `<packageSourceCredentials>` element contains child nodes for each applicable source name (spaces in the name are replaced with `_x0020+`).</span></span> <span data-ttu-id="d7b18-200">Es decir, para los orígenes denominados "Contoso" y "Test Source", el archivo de configuración contiene lo siguiente cuando se usan contraseñas cifradas:</span><span class="sxs-lookup"><span data-stu-id="d7b18-200">That is, for sources named "Contoso" and "Test Source", the config file contains the following when using encrypted passwords:</span></span>

```xml
<packageSourceCredentials>
    <Contoso>
        <add key="Username" value="user@contoso.com" />
        <add key="Password" value="..." />
    </Contoso>
    <Test_x0020_Source>
        <add key="Username" value="user" />
        <add key="Password" value="..." />
    </Test_x0020_Source>
</packageSourceCredentials>
```

<span data-ttu-id="d7b18-201">Cuando se usan contraseñas sin cifrar:</span><span class="sxs-lookup"><span data-stu-id="d7b18-201">When using unencrypted passwords:</span></span>

```xml
<packageSourceCredentials>
    <Contoso>
        <add key="Username" value="user@contoso.com" />
        <add key="ClearTextPassword" value="33f!!lloppa" />
    </Contoso>
    <Test_x0020_Source>
        <add key="Username" value="user" />
        <add key="ClearTextPassword" value="hal+9ooo_da!sY" />
    </Test_x0020_Source>
</packageSourceCredentials>
```

### <a name="apikeys"></a><span data-ttu-id="d7b18-202">apikeys</span><span class="sxs-lookup"><span data-stu-id="d7b18-202">apikeys</span></span>

<span data-ttu-id="d7b18-203">Almacena claves para los orígenes en los que se usa autenticación de clave de API, como se establece mediante el [comando `nuget setapikey`](../tools/cli-ref-setapikey.md).</span><span class="sxs-lookup"><span data-stu-id="d7b18-203">Stores keys for sources that use API key authentication, as set with the [`nuget setapikey` command](../tools/cli-ref-setapikey.md).</span></span>

| <span data-ttu-id="d7b18-204">Key</span><span class="sxs-lookup"><span data-stu-id="d7b18-204">Key</span></span> | <span data-ttu-id="d7b18-205">Valor</span><span class="sxs-lookup"><span data-stu-id="d7b18-205">Value</span></span> |
| --- | --- |
| <span data-ttu-id="d7b18-206">(dirección URL de origen)</span><span class="sxs-lookup"><span data-stu-id="d7b18-206">(source URL)</span></span> | <span data-ttu-id="d7b18-207">La clave de API cifrada.</span><span class="sxs-lookup"><span data-stu-id="d7b18-207">The encrypted API key.</span></span> |

<span data-ttu-id="d7b18-208">**Ejemplo**:</span><span class="sxs-lookup"><span data-stu-id="d7b18-208">**Example**:</span></span>

```xml
<apikeys>
    <add key="https://MyRepo/ES/api/v2/package" value="encrypted_api_key" />
</apikeys>
```

### <a name="disabledpackagesources"></a><span data-ttu-id="d7b18-209">disabledPackageSources</span><span class="sxs-lookup"><span data-stu-id="d7b18-209">disabledPackageSources</span></span>

<span data-ttu-id="d7b18-210">Orígenes actualmente deshabilitados identificados.</span><span class="sxs-lookup"><span data-stu-id="d7b18-210">Identified currently disabled sources.</span></span> <span data-ttu-id="d7b18-211">Puede estar vacía.</span><span class="sxs-lookup"><span data-stu-id="d7b18-211">May be empty.</span></span>

| <span data-ttu-id="d7b18-212">Key</span><span class="sxs-lookup"><span data-stu-id="d7b18-212">Key</span></span> | <span data-ttu-id="d7b18-213">Valor</span><span class="sxs-lookup"><span data-stu-id="d7b18-213">Value</span></span> |
| --- | --- |
| <span data-ttu-id="d7b18-214">(nombre del origen)</span><span class="sxs-lookup"><span data-stu-id="d7b18-214">(name of source)</span></span> | <span data-ttu-id="d7b18-215">Un valor booleano que indica si el origen está deshabilitado.</span><span class="sxs-lookup"><span data-stu-id="d7b18-215">A Boolean indicating whether the source is disabled.</span></span> |

<span data-ttu-id="d7b18-216">**Ejemplo:**</span><span class="sxs-lookup"><span data-stu-id="d7b18-216">**Example:**</span></span>

```xml
<disabledPackageSources>
    <add key="Contoso" value="true" />
</disabledPackageSources>

<!-- Empty list -->
<disabledPackageSources />
```

### <a name="activepackagesource"></a><span data-ttu-id="d7b18-217">activePackageSource</span><span class="sxs-lookup"><span data-stu-id="d7b18-217">activePackageSource</span></span>

<span data-ttu-id="d7b18-218">*(solo para 2.x; en desuso en 3.x y versiones posteriores)*</span><span class="sxs-lookup"><span data-stu-id="d7b18-218">*(2.x only; deprecated in 3.x+)*</span></span>

<span data-ttu-id="d7b18-219">Identifica al origen actualmente activo o indica la suma de todos los orígenes.</span><span class="sxs-lookup"><span data-stu-id="d7b18-219">Identifies to the currently active source or indicates the aggregate of all sources.</span></span>

| <span data-ttu-id="d7b18-220">Key</span><span class="sxs-lookup"><span data-stu-id="d7b18-220">Key</span></span> | <span data-ttu-id="d7b18-221">Valor</span><span class="sxs-lookup"><span data-stu-id="d7b18-221">Value</span></span> |
| --- | --- |
| <span data-ttu-id="d7b18-222">(nombre del origen) o `All`</span><span class="sxs-lookup"><span data-stu-id="d7b18-222">(name of source) or `All`</span></span> | <span data-ttu-id="d7b18-223">Si la clave es el nombre de un origen, el valor es la ruta de acceso o la dirección URL del origen.</span><span class="sxs-lookup"><span data-stu-id="d7b18-223">If key is the name of a source, the value is the source path or URL.</span></span> <span data-ttu-id="d7b18-224">Si es `All`, el valor debe ser `(Aggregate source)` para combinar todos los orígenes de paquetes que no estén deshabilitados.</span><span class="sxs-lookup"><span data-stu-id="d7b18-224">If `All`, value should be `(Aggregate source)` to combine all package sources that are not otherwise disabled.</span></span> |

<span data-ttu-id="d7b18-225">**Ejemplo**:</span><span class="sxs-lookup"><span data-stu-id="d7b18-225">**Example**:</span></span>

```xml
<activePackageSource>
    <!-- Only one active source-->
    <add key="nuget.org" value="https://api.nuget.org/v3/index.json" />

    <!-- All non-disabled sources are active -->
    <add key="All" value="(Aggregate source)" />
</activePackageSource>
```

## <a name="using-environment-variables"></a><span data-ttu-id="d7b18-226">Uso de variables de entorno</span><span class="sxs-lookup"><span data-stu-id="d7b18-226">Using environment variables</span></span>

<span data-ttu-id="d7b18-227">Puede usar variables de entorno en valores `NuGet.Config` (NuGet 3.4 o versiones posteriores) para aplicar la configuración en tiempo de ejecución.</span><span class="sxs-lookup"><span data-stu-id="d7b18-227">You can use environment variables in `NuGet.Config` values (NuGet 3.4+) to apply settings at run time.</span></span>

<span data-ttu-id="d7b18-228">Por ejemplo, si la variable de entorno `HOME` en Windows se establece en `c:\users\username`, el valor de `%HOME%\NuGetRepository` en el archivo de configuración se resuelve como `c:\users\username\NuGetRepository`.</span><span class="sxs-lookup"><span data-stu-id="d7b18-228">For example, if the `HOME` environment variable on Windows is set to `c:\users\username`, then the value of `%HOME%\NuGetRepository` in the configuration file resolves to `c:\users\username\NuGetRepository`.</span></span>

<span data-ttu-id="d7b18-229">De forma similar, si `HOME` en Mac/Linux se establece en `/home/myStuff`, `$HOME/NuGetRepository` en el archivo de configuración se resuelve como `/home/myStuff/NuGetRepository`.</span><span class="sxs-lookup"><span data-stu-id="d7b18-229">Similarly, if `HOME` on Mac/Linux is set to `/home/myStuff`, then `$HOME/NuGetRepository` in the configuration file resolves to `/home/myStuff/NuGetRepository`.</span></span>

<span data-ttu-id="d7b18-230">Si no se encuentra una variable de entorno, NuGet usa el valor literal del archivo de configuración.</span><span class="sxs-lookup"><span data-stu-id="d7b18-230">If an environment variable is not found, NuGet uses the literal value from the configuration file.</span></span>

## <a name="example-config-file"></a><span data-ttu-id="d7b18-231">Archivo de configuración de ejemplo</span><span class="sxs-lookup"><span data-stu-id="d7b18-231">Example config file</span></span>

<span data-ttu-id="d7b18-232">A continuación se muestra un archivo `NuGet.Config` de ejemplo en el que se ilustran varios valores:</span><span class="sxs-lookup"><span data-stu-id="d7b18-232">Below is an example `NuGet.Config` file that illustrates a number of settings:</span></span>

```xml
<?xml version="1.0" encoding="utf-8"?>
<configuration>
    <config>
        <!--
            Used to specify the default location to expand packages.
            See: nuget.exe help install
            See: nuget.exe help update

            In this example, %PACKAGEHOME% is an environment variable. On Mac/Linux,
            use $PACKAGE_HOME/External as the value.
        -->
        <add key="repositoryPath" value="%PACKAGEHOME%\External" />

        <!--
            Used to specify default source for the push command.
            See: nuget.exe help push
        -->

        <add key="defaultPushSource" value="https://MyRepo/ES/api/v2/package" />

        <!-- Proxy settings -->
        <add key="http_proxy" value="host" />
        <add key="http_proxy.user" value="username" />
        <add key="http_proxy.password" value="encrypted_password" />
    </config>

    <packageRestore>
        <!-- Allow NuGet to download missing packages -->
        <add key="enabled" value="True" />

        <!-- Automatically check for missing packages during build in Visual Studio -->
        <add key="automatic" value="True" />
    </packageRestore>

    <!--
        Used to specify the default Sources for list, install and update.
        See: nuget.exe help list
        See: nuget.exe help install
        See: nuget.exe help update
    -->
    <packageSources>
        <add key="NuGet official package source" value="https://api.nuget.org/v3/index.json" />
        <add key="MyRepo - ES" value="https://MyRepo/ES/nuget" />
    </packageSources>

    <!-- Used to store credentials -->
    <packageSourceCredentials />

    <!-- Used to disable package sources  -->
    <disabledPackageSources />

    <!--
        Used to specify default API key associated with sources.
        See: nuget.exe help setApiKey
        See: nuget.exe help push
        See: nuget.exe help mirror
    -->
    <apikeys>
        <add key="https://MyRepo/ES/api/v2/package" value="encrypted_api_key" />
    </apikeys>
</configuration>
```