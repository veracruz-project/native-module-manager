# Native module sandboxer

A program based on [Google's Sandboxed API](https://github.com/google/sandboxed-api) that sets up a sandbox environment for Veracruz native modules and executes them. It is called by the Runtime Manager everytime a WebAssembly program invokes a dynamic native module, or whenever a participant directly invokes a native program (provisioned native module).  
If you are running the sandboxer in Docker, you should consider passing `--init` to Docker, or the fork server will end up producing zombie processes whose status never gets reaped.

## Example usage
```
native-module-sandboxer
  --sandbox2tool_resolve_and_add_libraries
  --sandbox2tool_mount_tmp
  --sandbox2tool_additional_bind_mounts "/tmp/nmm/tflite-nm/input=>/input,/tmp/nmm/tflite-nm/program_internal=>/program_internal"
  tflite-nm
```


