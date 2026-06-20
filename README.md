{
  "name": "lexcity",
  "version": "1.0.0",
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "tsc && vite build",
    "preview": "vite preview"
  },
  "dependencies": {
    "@react-three/drei": "^9.0.0",
    "@react-three/fiber": "^8.0.0",
    "@tanstack/react-query": "^5.0.0",
    "framer-motion": "^11.0.0",
    "lucide-react",
    "react": "^18.0.0",
    "react-dom": "^18.0.0",
    "three": "^0.160.0",
    "wouter": "^3.0.0"
  },
  "devDependencies": {
    "@types/react": "^18.0.0",
    "@types/react-dom": "^18.0.0",
    "@types/three": "^0.160.0",
    "@vitejs/plugin-react": "^4.0.0",
    "autoprefixer": "^10.0.0",
    "tailwindcss": "^3.0.0",
    "typescript": "^5.0.0",
    "vite": "^5.0.0"
  }
}
<!DOCTYPE html>
<html lang="en">
  <head>
    <meta charset="UTF-8" />
    <meta name="viewport" content="width=device-width, initial-scale=1.0" />
    <title>LexCity — Where the Law Bends</title>
  </head>
  <body>
    <div id="root"></div>
    <script type="module" src="/src/main.tsx"></script>
  </body>
</html>
import { createRoot } from "react-dom/client";
import App from "./App";
import "./index.css";

createRoot(document.getElementById("root")!).render(<
import { Switch, Route } from "wouter";
import { QueryClient, QueryClientProvider } from "@tanstack/react-query";
import { Home } from "./pages/Home";

const queryClient = new QueryClient();

function Router() {
  return (
    <Switch>
      <Route path="/" component={Home} />
    </Switch>
  );
}

function App() {
  return (
    <QueryClientProvider client={queryClient}>
      <Router />
    </QueryClientProvider>
  );
}

export default App;
@import url('https://fonts.googleapis.com/css2?family=EB+Garamond:ital,wght@0,400..800;1,400..800&family=Inter:wght@400;500;600&display=swap');
@tailwind base;
@tailwind components;
@tailwind utilities;

:root {
  --background: #0a0a0f;
  --foreground: #ebebeb;
  --card: #0d0d14;
  --border: #1a1a26;
  --primary: #c41e3a;
  --gold: #b8960c;
  --muted: #888888;
}

* { box-sizing: border-box; margin: 0; padding: 0; }

body {
  background-color: var(--background);
  color: var(--foreground);
  font-family: 'Inter', sans-serif;
  -webkit-font-smoothing: antialiased;
}
import { motion } from "framer-motion";
import { ScalesScene } from "../components/ScalesScene";
import { GavelScene } from "../components/GavelScene";
import { BarChartScene } from "../components/BarChartScene";
import { FlipCard } from "../components/FlipCard";
import { WebGLErrorBoundary } from "../components/WebGLErrorBoundary";

const cases = [
  { caseName: "Ewing v. California", year: "2003", summary: "Upheld 25 years to life for stealing golf clubs under three-strikes law.", severity: "Systemic" as const },
  { caseName: "Kalief Browder", year: "2010", summary: "3 years in Rikers Island, no trial, no conviction, age 16.", severity: "Individual" as const },
  { caseName: "Central Park Five", year: "1989", summary: "Five teenagers wrongfully convicted after police coerced false confessions.", severity: "Systemic" as const },
  { caseName: "Martin Luther King Jr.", year: "1955–1968", summary: "Jailed 29 times for nonviolent civil disobedience against unjust laws.", severity: "Individual" as const },
  { caseName: "Citizens United v. FEC", year: "2010", summary: "Granted corporations unlimited political spending rights as free speech.", severity: "Corporate" as const },
  { caseName: "Shelby County v. Holder", year: "2013", summary: "Gutted the Voting Rights Act, enabling immediate voter suppression laws.", severity: "Systemic" as const },
];

export function Home() {
  return (
    <div style={{ background: "#0a0a0f", minHeight: "100vh", color: "#ebebeb", overflowX: "hidden" }}>

      {/* HERO */}
      <section style={{ position: "relative", height: "100vh", display: "flex", alignItems: "center", justifyContent: "center" }}>
        <WebGLErrorBoundary fallback={<div style={{ position: "absolute", inset: 0, background: "linear-gradient(to bottom, #0a0a0f, #0d0d14)" }} />}>
          <ScalesScene />
        </WebGLErrorBoundary>
        <div style={{ position: "relative", zIndex: 10, textAlign: "center", padding: "0 24px", maxWidth: 900 }}>
          <motion.h1 initial={{ opacity: 0, y: 30 }} animate={{ opacity: 1, y: 0 }} transition={{ duration: 1, delay: 0.5 }}
            style={{ fontSize: "clamp(4rem, 12vw, 9rem)", fontFamily: "'EB Garamond', serif", fontWeight: 700, letterSpacing: "-0.02em", lineHeight: 1 }}>
            LEX<span style={{ color: "#c41e3a" }}>CITY</span>
          </motion.h1>
          <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} transition={{ delay: 1.2 }}
            style={{ height: 1, width: 96, background: "#c41e3a", margin: "24px auto" }} />
          <motion.p initial={{ opacity: 0 }} animate={{ opacity: 1 }} transition={{ delay: 1.5 }}
            style={{ fontSize: "1.25rem", color: "#888", letterSpacing: "0.15em", textTransform: "uppercase", fontFamily: "monospace" }}>
            Where the Law Bends
          </motion.p>
          <motion.p initial={{ opacity: 0 }} animate={{ opacity: 1 }} transition={{ delay: 2 }}
            style={{ marginTop: 16, color: "#555", fontSize: "0.95rem" }}>
            Documenting inequality in the justice system.
          </motion.p>
        </div>
        <motion.div initial={{ opacity: 0 }} animate={{ opacity: 1 }} transition={{ delay: 3 }}
          style={{ position: "absolute", bottom: 40, left: "50%", transform: "translateX(-50%)" }}>
          <div style={{ width: 1, height: 64, background: "linear-gradient(to bottom, #c41e3a, transparent)" }} />
        </motion.div>
      </section>

      {/* STATISTICS */}
      <section style={{ padding: "128px 24px", background: "#0d0d14" }}>
        <div style={{ maxWidth: 1200, margin: "0 auto", display: "grid", gridTemplateColumns: "1fr 1fr", gap: 64, alignItems: "center" }}>
          <motion.div initial={{ opacity: 0, x: -50 }} whileInView={{ opacity: 1, x: 0 }} viewport={{ once: true }} transition={{ duration: 0.8 }}>
            <h2 style={{ fontSize: "clamp(2rem, 4vw, 3rem)", fontFamily: "'EB Garamond', serif", fontWeight: 700, marginBottom: 48 }}>
              <span style={{ color: "#c41e3a" }}>01.</span> The Broken Scale
            </h2>
            {[
              { stat: "97%", text: "Of federal cases resolved by plea bargains — pressuring the poor to plead guilty." },
              { stat: "5.9x", text: "Longer sentences received by Black men vs. white men for similar crimes." },
              { stat: "7 min", text: "Average prep time per misdemeanor case for underfunded public defenders." },
            ].map(({ stat, text }) => (
              <div key={stat} style={{ borderLeft: "2px solid #1a1a26", paddingLeft: 24, marginBottom: 48 }}>
                <div style={{ fontSize: "clamp(3rem, 5vw, 4rem)", fontWeight: 700, fontFamily: "monospace", color: "#b8960c" }}>{stat}</div>
                <p style={{ color: "#888", marginTop: 8, lineHeight: 1.6 }}>{text}</p>
              </div>
            ))}
          </motion.div>
          <div style={{ height: 500 }}>
            <WebGLErrorBoundary><GavelScene /></WebGLErrorBoundary>
          </div>
        </div>
      </section>

      {/* CASE FILES */}
      <section style={{ padding: "128px 24px", background: "#0a0a0f" }}>
        <div style={{ maxWidth: 1200, margin: "0 auto" }}>
          <motion.div initial={{ opacity: 0, y: 30 }} whileInView={{ opacity: 1, y: 0 }} viewport={{ once: true }} style={{ marginBottom: 64 }}>
            <h2 style={{ fontSize: "clamp(2rem, 4vw, 3rem)", fontFamily: "'EB Garamond', serif", fontWeight: 700 }}>
              <span style={{ color: "#c41e3a" }}>02.</span> Case Files
            </h2>
            <p style={{ color: "#888", fontStyle: "italic", marginTop: 16, fontFamily: "'EB Garamond', serif", fontSize: "1.2rem" }}>Landmarks of unequal justice.</p>
          </motion.div>
          <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fill, minmax(300px, 1fr))", gap: 32 }}>
            {cases.map((c, i) => (
              <motion.div key={c.caseName} initial={{ opacity: 0, y: 50 }} whileInView={{ opacity: 1, y: 0 }} viewport={{ once: true }} transition={{ delay: i * 0.1 }}>
                <FlipCard {...c} />
              </motion.div>
            ))}
          </div>
        </div>
      </section>

      {/* 3D BAR CHART */}
      <section style={{ padding: "128px 24px", background: "#0d0d14", borderTop: "1px solid #1a1a26", borderBottom: "1px solid #1a1a26" }}>
        <div style={{ maxWidth: 1200, margin: "0 auto" }}>
          <motion.div initial={{ opacity: 0, y: 30 }} whileInView={{ opacity: 1, y: 0 }} viewport={{ once: true }} style={{ textAlign: "center", marginBottom: 48 }}>
            <h2 style={{ fontSize: "clamp(2rem, 4vw, 3rem)", fontFamily: "'EB Garamond', serif", fontWeight: 700, marginBottom: 16 }}>The Price of Justice</h2>
            <p style={{ color: "#888", fontSize: "1.1rem" }}>Access to capital directly correlates to legal outcomes.</p>
          </motion.div>
          <div style={{ borderRadius: 16, overflow: "hidden", border: "1px solid #1a1a26" }}>
            <WebGLErrorBoundary><BarChartScene /></WebGLErrorBoundary>
          </div>
        </div>
      </section>

      {/* QUOTES */}
      <section style={{ padding: "128px 24px", background: "#0a0a0f" }}>
        <div style={{ maxWidth: 860, margin: "0 auto" }}>
          {[
            { quote: "Injustice anywhere is a threat to justice everywhere.", author: "Martin Luther King Jr." },
            { quote: "The law, in its majestic equality, forbids the rich as well as the poor to sleep under bridges.", author: "Anatole France" },
            { quote: "We have a criminal justice system that treats you better if you are rich and guilty than if you are poor and innocent.", author: "Bryan Stevenson" },
          ].map((q, i) => (
            <motion.div key={i} initial={{ opacity: 0, scale: 0.95 }} whileInView={{ opacity: 1, scale: 1 }} viewport={{ once: true }} transition={{ duration: 0.8 }}
              style={{ textAlign: "center", marginBottom: 96 }}>
              <p style={{ fontSize: "clamp(1.5rem, 3vw, 2.5rem)", fontFamily: "'EB Garamond', serif", lineHeight: 1.4, color: "#ebebeb" }}>"{q.quote}"</p>
              <p style={{ color: "#c41e3a", fontFamily: "monospace", letterSpacing: "0.15em", textTransform: "uppercase", fontSize: "0.8rem", marginTop: 24 }}>— {q.author}</p>
            </motion.div>
          ))}
        </div>
      </section>

      {/* TAKE ACTION */}
      <section style={{ padding: "128px 24px", background: "#0d0d14", borderTop: "1px solid #1a1a26" }}>
        <div style={{ maxWidth: 900, margin: "0 auto", textAlign: "center" }}>
          <motion.h2 initial={{ opacity: 0, y: 20 }} whileInView={{ opacity: 1, y: 0 }} viewport={{ once: true }}
            style={{ fontSize: "clamp(3rem, 7vw, 5rem)", fontFamily: "'EB Garamond', serif", fontWeight: 700, marginBottom: 24 }}>
            The Verdict is Yours.
          </motion.h2>
          <p style={{ color: "#888", fontSize: "1.1rem", marginBottom: 64 }}>Silence is compliance. The system relies on you looking away.</p>
          <div style={{ display: "grid", gridTemplateColumns: "repeat(auto-fill, minmax(220px, 1fr))", gap: 24 }}>
            {[{ n: 1, title: "Learn", desc: "Understand local laws and systemic issues." }, { n: 2, title: "Share", desc: "Amplify the stories of those silenced." }, { n: 3, title: "Advocate", desc: "Support legal defense funds and reform." }].map((a) => (
              <motion.div key={a.title} initial={{ opacity: 0, y: 30 }} whileInView={{ opacity: 1, y: 0 }} viewport={{ once: true }}
                style={{ padding: 32, border: "1px solid #1a1a26", borderRadius: 12, background: "#0a0a0f", display: "flex", flexDirection: "column", alignItems: "center", gap: 16 }}>
                <span style={{ color: "#c41e3a", fontFamily: "'EB Garamond', serif", fontStyle: "italic", fontSize: "2rem" }}>{a.n}.</span>
                <h3 style={{ fontSize: "1.5rem", fontFamily: "'EB Garamond', serif", fontWeight: 700 }}>{a.title}</h3>
                <p style={{ color: "#666", fontSize: "0.9rem" }}>{a.desc}</p>
              </motion.div>
            ))}
          </div>
        </div>
      </section>

      <footer style={{ padding: "48px 24px", textAlign: "center", color: "#333", fontFamily: "monospace", fontSize: "0.8rem", borderTop: "1px solid #1a1a26" }}>
        LEXCITY © {new Date().getFullYear()} // NO JUSTICE WITHOUT TRUTH
      </footer>
    </div>
  );
}
import React from "react";

interface State { hasError: boolean; }

export class WebGLErrorBoundary extends React.Component<{ children: React.ReactNode; fallback?: React.ReactNode }, State> {
  constructor(props: { children: React.ReactNode; fallback?: React.ReactNode }) {
    super(props);
    this.state = { hasError: false };
  }
  static getDerivedStateFromError() { return { hasError: true }; }
  render() {
    if (this.state.hasError) return this.props.fallback ?? <div style={{ padding: 32, color: "#555", textAlign: "center" }}>3D not supported in this environment</div>;
    return this.props.children;
  }
}
import React, { useRef } from "react";
import { Canvas, useFrame } from "@react-three/fiber";
import { Float, Environment } from "@react-three/drei";
import * as THREE from "three";

function Scales() {
  const group = useRef<THREE.Group>(null);
  useFrame((state) => {
    if (group.current) {
      group.current.rotation.y = Math.sin(state.clock.elapsedTime * 0.2) * 0.1;
      group.current.position.y = Math.sin(state.clock.elapsedTime * 0.5) * 0.2;
    }
  });
  return (
    <group ref={group}>
      <mesh position={[0, -4, 0]}><cylinderGeometry args={[2, 2.5, 0.5, 32]} /><meshStandardMaterial color="#b8960c" metalness={0.8} roughness={0.2} /></mesh>
      <mesh position={[0, 0, 0]}><cylinderGeometry args={[0.3, 0.4, 8, 32]} /><meshStandardMaterial color="#b8960c" metalness={0.8} roughness={0.2} /></mesh>
      <group position={[0, 3.8, 0]} rotation={[0, 0, 0.4]}>
        <mesh><boxGeometry args={[8, 0.3, 0.3]} /><meshStandardMaterial color="#b8960c" metalness={0.8} roughness={0.2} /></mesh>
        <group position={[-3.8, -0.15, 0]}>
          <mesh position={[0, -4, 0]} rotation={[Math.PI / 2, 0, 0]}><torusGeometry args={[1.5, 0.1, 16, 32]} /><meshStandardMaterial color="#b8960c" metalness={0.8} roughness={0.2} /></mesh>
          <mesh position={[0, -3, 0]}><boxGeometry args={[1.5, 2, 1.5]} /><meshStandardMaterial color="#2d2d2d" roughness={0.9} /></mesh>
          <mesh position={[0, -1.8, 0]}><boxGeometry args={[0.5, 0.5, 0.5]} /><meshStandardMaterial color="#b8960c" metalness={0.5} roughness={0.5} /></mesh>
        </group>
        <group position={[3.8, -0.15, 0]}>
          <mesh position={[0, -4, 0]} rotation={[Math.PI / 2, 0, 0]}><torusGeometry args={[1.5, 0.1, 16, 32]} /><meshStandardMaterial color="#b8960c" metalness={0.8} roughness={0.2} /></mesh>
          <mesh position={[0, -3.5, 0]}><cylinderGeometry args={[0.3, 0.3, 1]} /><meshStandardMaterial color="#888888" roughness={0.7} /></mesh>
          <mesh position={[0, -2.8, 0]}><sphereGeometry args={[0.3]} /><meshStandardMaterial color="#888888" roughness={0.7} /></mesh>
        </group>
      </group>
    </group>
  );
}

export function ScalesScene() {
  return (
    <div style={{ position: "absolute", inset: 0, zIndex: -1 }}>
      <Canvas camera={{ position: [0, 2, 18], fov: 45 }}>
        <fog attach="fog" args={["#0a0a0f", 10, 40]} />
        <ambientLight intensity={0.2} />
        <directionalLight position={[-10, 10, 5]} intensity={1.5} />
        <pointLight position={[10, 5, -5]} intensity={2} color="#c41e3a" />
        <React.Suspense fallback={null}>
          <Float speed={2} rotationIntensity={0.5} floatIntensity={1}><Scales /></Float>
          <Environment preset="city" />
        </React.Suspense>
      </Canvas>
    </div>
  );
}
import React, { useRef } from "react";
import { Canvas, useFrame } from "@react-three/fiber";
import { Float, Environment } from "@react-three/drei";
import * as THREE from "three";

function Gavel() {
  const group = useRef<THREE.Group>(null);
  useFrame((state) => {
    if (group.current) {
      group.current.rotation.y += 0.01;
      group.current.rotation.z = Math.sin(state.clock.elapsedTime * 2) * 0.1 - 0.2;
    }
  });
  return (
    <group ref={group} rotation={[0.4, 0, 0]}>
      <mesh position={[0, -1.5, 0]}><cylinderGeometry args={[0.15, 0.2, 4, 32]} /><meshStandardMaterial color="#4a3b22" roughness={0.8} /></mesh>
      <mesh position={[0, 0.2, 0]} rotation={[0, 0, Math.PI / 2]}><cylinderGeometry args={[0.4, 0.4, 1.8, 32]} /><meshStandardMaterial color="#3d2e16" roughness={0.7} /></mesh>
      <mesh position={[1.1, 0.2, 0]} rotation={[0, 0, Math.PI / 2]}><cylinderGeometry args={[0.5, 0.4, 0.4, 32]} /><meshStandardMaterial color="#4a3b22" roughness={0.7} /></mesh>
      <mesh position={[-1.1, 0.2, 0]} rotation={[0, 0, Math.PI / 2]}><cylinderGeometry args={[0.4, 0.5, 0.4, 32]} /><meshStandardMaterial color="#4a3b22" roughness={0.7} /></mesh>
    </group>
  );
}

export function GavelScene() {
  return (
    <div style={{ width: "100%", height: "100%", minHeight: 400 }}>
      <Canvas camera={{ position: [0, 0, 8], fov: 45 }}>
        <ambientLight intensity={0.3} />
        <directionalLight position={[5, 5, 5]} intensity={1.5} />
        <pointLight position={[-5, -5, -5]} intensity={0.5} color="#c41e3a" />
        <React.Suspense fallback={null}>
          <Float speed={2} rotationIntensity={0.5} floatIntensity={1}><Gavel /></Float>
          <Environment preset="city" />
        </React.Suspense>
      </Canvas>
    </div>
  );
}
import React, { useRef } from "react";
import { Canvas, useFrame } from "@react-three/fiber";
import { OrbitControls, Environment, Text } from "@react-three/drei";
import * as THREE from "three";

function ChartBars() {
  const group = useRef<THREE.Group>(null);
  useFrame((state) => { if (group.current) group.current.rotation.y = Math.sin(state.clock.elapsedTime * 0.1) * 0.2; });
  return (
    <group ref={group} position={[0, -2, 0]}>
      <group position={[-2, 0, 0]}>
        <mesh position={[0, 1, 0]}><boxGeometry args={[1.5, 2, 1.5]} /><meshStandardMaterial color="#888888" roughness={0.6} /></mesh>
        <Text position={[0, 2.5, 0]} fontSize={0.4} color="#ffffff" anchorX="center" anchorY="middle">$5,000</Text>
        <Text position={[0, -0.5, 0]} fontSize={0.3} color="#aaaaaa" anchorX="center" anchorY="middle">Public Defender</Text>
      </group>
      <group position={[2, 0, 0]}>
        <mesh position={[0, 4, 0]}><boxGeometry args={[1.5, 8, 1.5]} /><meshStandardMaterial color="#c41e3a" roughness={0.4} metalness={0.5} /></mesh>
        <Text position={[0, 8.5, 0]} fontSize={0.4} color="#ffffff" anchorX="center" anchorY="middle">$45,000+</Text>
        <Text position={[0, -0.5, 0]} fontSize={0.3} color="#aaaaaa" anchorX="center" anchorY="middle">Private Attorney</Text>
      </group>
      <mesh position={[0, -0.1, 0]}><boxGeometry args={[8, 0.2, 4]} /><meshStandardMaterial color="#111111" roughness={0.9} /></mesh>
    </group>
  );
}

export function BarChartScene() {
  return (
    <div style={{ width: "100%", height: 500 }}>
      <Canvas camera={{ position: [0, 4, 12], fov: 45 }}>
        <ambientLight intensity={0.4} />
        <directionalLight position={[10, 10, 10]} intensity={1.5} />
        <pointLight position={[-10, 5, -10]} intensity={2} color="#b8960c" />
        <React.Suspense fallback={null}>
          <ChartBars />
          <OrbitControls enableZoom={false} enablePan={false} autoRotate autoRotateSpeed={0.5} maxPolarAngle={Math.PI / 2} minPolarAngle={Math.PI / 4} />
          <Environment preset="city" />
        </React.Suspense>
      </Canvas>
    </div>
  );
}
interface FlipCardProps {
  caseName: string;
  year: string;
  summary: string;
  severity: "Systemic" | "Individual" | "Corporate";
}

const badgeColors: Record<string, string> = {
  Systemic: "#7f1d1d",
  Corporate: "#713f12",
  Individual: "#1e293b",
};

export function FlipCard({ caseName, year, summary, severity }: FlipCardProps) {
  return (
    <div style={{ height: 256, perspective: 1000 }} className="group">
      <div style={{ position: "relative", height: "100%", transition: "transform 0.5s", transformStyle: "preserve-3d" }} className="group-hover:[transform:rotateY(180deg)]">
        <div style={{ position: "absolute", inset: 0, borderRadius: 12, background: "#0d0d14", border: "1px solid #1a1a26", padding: 24, backfaceVisibility: "hidden", display: "flex", flexDirection: "column", justifyContent: "space-between" }}>
          <div>
            <div style={{ display: "flex", justifyContent: "space-between", marginBottom: 16 }}>
              <span style={{ fontSize: "0.8rem", fontFamily: "monospace", color: "#555" }}>{year}</span>
              <span style={{ padding: "2px 10px", borderRadius: 9999, background: badgeColors[severity], color: "#ddd", fontSize: "0.7rem" }}>{severity}</span>
            </div>
            <h3 style={{ fontSize: "1.4rem", fontFamily: "'EB Garamond', serif", fontWeight: 700, lineHeight: 1.3 }}>{caseName}</h3>
          </div>
          <div style={{ display: "flex", alignItems: "center", gap: 8, fontSize: "0.75rem", color: "#555", textTransform: "uppercase", letterSpacing: "0.12em" }}>
            <div style={{ width: 16, height: 1, background: "#c41e3a" }} /> View File
          </div>
        </div>
        <div style={{ position: "absolute", inset: 0, borderRadius: 12, background: "#13131e", border: "1px solid #1a1a26", padding: 24, transform: "rotateY(180deg)", backfaceVisibility: "hidden", display: "flex", alignItems: "center" }}>
          <div>
            <p style={{ fontSize: "0.7rem", fontFamily: "monospace", color: "#555", marginBottom: 8, textTransform: "uppercase" }}>Verdict / Impact</p>
            <p style={{ lineHeight: 1.6, color: "#ccc" }}>{summary}</p>
          </div>
        </div>
      </div>
    </div>
  );
}