![readme-header-dark](https://user-images.githubusercontent.com/3797215/156384064-08a889d6-73c0-4cbf-8ff3-28dc601d1f5f.svg#gh-dark-mode-only)
![readme-header](https://user-images.githubusercontent.com/3797215/156259138-fb9f59f8-52f2-474a-b78c-6570867e4ead.svg#gh-light-mode-only)

<div align="center">

![GitHub License MIT](https://img.shields.io/github/license/wbkd/react-flow?color=%23ff0072)
![npm downloads](https://img.shields.io/npm/dt/reactflow?color=%23FF0072&label=downloads)
![GitHub Repo stars](https://img.shields.io/github/stars/wbkd/react-flow?color=%23FF0072)
![GitHub release (latest by date)](https://img.shields.io/github/v/release/wbkd/react-flow?color=%23FF0072)

A highly customizable React component for building interactive graphs and node-based editors.

[🚀 Getting Started](https://reactflow.dev/docs/quickstart/) | [📖 Documentation](https://reactflow.dev/docs/api/react-flow-props) | [📺 Examples](https://reactflow.dev/docs/examples/overview) | [☎️ Discord](https://discord.gg/RVmnytFmGW) | [💎 React Flow Pro](https://pro.reactflow.dev)

</div>

---

## Key Features

- **Easy to use:** Seamless zooming and panning, single- and multi selection of graph elements and keyboard shortcuts are supported out of the box
- **Customizable:** Different [node](https://reactflow.dev/docs/api/nodes/node-types) and [edge types](https://reactflow.dev/docs/api/edges/edge-types) and support for custom nodes with multiple handles and custom edges
- **Fast rendering:** Only nodes that have changed are re-rendered and only those in the viewport are displayed
- **Hooks and Utils:** [Hooks](https://reactflow.dev/docs/api/hooks/use-react-flow) for handling nodes, edges and the viewport and graph [helper functions](https://reactflow.dev/docs/api/graph-util-functions)
- **Plugin Components:** [Background](https://reactflow.dev/docs/api/plugin-components/background), [MiniMap](https://reactflow.dev/docs/api/plugin-components/minimap) and [Controls](https://reactflow.dev/docs/api/plugin-components/controls)
- **Reliable**: Written in [Typescript](https://www.typescriptlang.org/) and tested with [cypress](https://www.cypress.io/)

## Commercial Usage

**Are you using React Flow for a personal project?** Great! No sponsorship needed, you can support us by reporting any bugs you find, sending us screenshots of your projects, and starring us on Github 🌟

**Are you using React Flow at your organization and making money from it?** Awesome! We rely on your support to keep React Flow developed and maintained under an MIT License, just how we like it. You can do that on the [React Flow Pro website](https://pro.reactflow.dev) or through [Github Sponsors](https://github.com/sponsors/wbkd).

You can find more information in our [React Flow Pro FAQs](https://pro.reactflow.dev/info).

## Installation

The easiest way to get the latest version of React Flow is to install it via npm, yarn or pnpm:

```bash
npm install reactflow
```

## Quickstart

This is only a very basic usage example of React Flow. To see everything that is possible with the library, please refer to the [website](https://reactflow.dev) for [guides](https://reactflow.dev/docs/guides/custom-nodes), [examples](https://reactflow.dev/docs/examples/overview) and the full [API reference](https://reactflow.dev/docs/api/react-flow-props).

```jsx
import { useCallback } from 'react';
import ReactFlow, {
  MiniMap,
  Controls,
  Background,
  useNodesState,
  useEdgesState,
  addEdge,
} from 'reactflow';

import 'reactflow/dist/style.css';

const initialNodes = [
  { id: '1', position: { x: 0, y: 0 }, data: { label: '1' } },
  { id: '2', position: { x: 0, y: 100 }, data: { label: '2' } },
  { id: '2', position: { x: 0, y: 100 }, data: { label: '2' } },
];

const initialEdges = [{ id: 'e1-2', source: '1', target: '2' }];

function Flow() {
  const [nodes, setNodes, onNodesChange] = useNodesState(initialNodes);
  const [edges, setEdges, onEdgesChange] = useEdgesState(initialEdges);

  const onConnect = useCallback((params) => setEdges((eds) => addEdge(params, eds)), [setEdges]);

  return (
    <ReactFlow
      nodes={nodes}
      edges={edges}
      onNodesChange={onNodesChange}
      onEdgesChange={onEdgesChange}
      onConnect={onConnect}
    >
      <MiniMap />
      <Controls />
      <Background />
    </ReactFlow>
  );
}

export default Flow;
```

## Development

Before you can start developing please make sure that you have [pnpm](https://pnpm.io/) installed (`npm i -g pnpm`). Then install the dependencies using pnpm: `pnpm install`.

Run `pnpm build` once and then you can use `pnpm dev` for local development.

## Testing

Testing is done with cypress. You can find the tests in the [`examples/cypress`](/examples/cypress/) folder. In order to run the tests do:

```sh
pnpm test
```

## Maintainers

React Flow is the full-time project of Moritz and Christopher of [webkid](https://webkid.io/), based in Berlin. If you need help or want to talk to us about a collaboration, reach out through our [contact form](https://pro.reactflow.dev/contact) or by joining the [React Flow Discord Server](https://discord.gg/Bqt6xrs).

- Moritz Klack • [Twitter](https://twitter.com/moklick) • [Github](https://github.com/moklick)
- Christopher Möller • [Twitter](https://twitter.com/chrtze) • [Github](https://github.com/chrtze)

Any support you provide goes directly towards the development and maintenance of React Flow, allowing us to continue to operate as an independent company, working on what we think is best for React Flow as an open-source library.

## Community Packages

- [useUndoable](https://github.com/xplato/useUndoable) - Hook for undo/redo functionality with an explicit React Flow example
- [react-flow-smart-edge](https://github.com/tisoap/react-flow-smart-edge) - Custom edge that doesn't intersect with nodes
- [Feliz.ReactFlow](https://github.com/tforkmann/Feliz.ReactFlow) - Feliz React Bindings for React Flow

## Credits

React Flow was initially developed for [datablocks](https://datablocks.pro), a graph-based editor for transforming, analyzing and visualizing data in the browser. Under the hood, React Flow depends on these great libraries:

- [d3-zoom](https://github.com/d3/d3-zoom) - used for zoom, pan and drag interactions with the graph canvas
- [d3-drag](https://github.com/d3/d3-drag) - used for making the nodes draggable
- [zustand](https://github.com/pmndrs/zustand) - internal state management

## License

React Flow is [MIT licensed](https://github.com/wbkd/react-flow/blob/main/LICENSE).
