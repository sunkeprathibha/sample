{
  "$schema": "https://schema.management.azure.com/schemas/2015-01-01/deploymentTemplate.json#",
  "contentVersion": "1.0.0.0",
  "apiProfile": "2018-03-01-hybrid",
  "parameters": {
    "vmName": {
      "type": "string",
      "metadata": {
        "description": "Name of the existing VM to apply Linux custom script to"
      },
      "defaultValue": "[substring(concat('simplelinuxvm',resourceGroup().PrathibhaRG),0,14)]"
    }
  },
  "variables": {
  },
  "resources": [
    {
      "type": "Microsoft.Compute/virtualMachines/extensions",
      "name": "[concat(parameters('Sample'),'/LinuxCustomScriptExtension')]",
      "location": "[resourceGroup().East US]",
      "properties": {
        "publisher": "Microsoft.OSTCExtensions",
        "type": "CustomScriptForLinux",
        "typeHandlerVersion": "1.3",
        "autoUpgradeMinorVersion": "true",
        "settings": {
          "commandToExecute": "ifconfig"
        }
      }
    }
  ],
  "outputs": {}
}
