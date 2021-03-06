# slab-pool 
[![Build Status](https://drone.io/github.com/jeffyang28/slab_pool/status.png)](https://drone.io/github.com/jeffyang28/slab_pool/latest)
[![Coverage Status](https://coveralls.io/repos/jeffyang28/slab_pool/badge.svg?branch=master&service=github)](https://coveralls.io/github/jeffyang28/slab_pool?branch=master)

## Introduction
 * Yet another slab allocator in golang
 * Desgin for reducing GC delay by reducing number of objects 

## Usage
    // Create slab pool
    slabPool, err := CreateSlabPool(4096, 128, 1024, 2)

    // Allocate chunk
    chunk, err := slabPool.Get(500)

    // Release chunk
    err := slabPool.Put(chunk)

    // Chunk reference operations
    chunk2, err := slabPool.Get(500)
    slabPool.IncRef(chunk2)
    slabPool.DecRef(chunk2)

## Limitation
 * Must Not append() on chunk allocated.

## License
Apache License Version 2.0
