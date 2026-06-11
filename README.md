name": "LexCity",
"version": "1.0.0",
"private": true,
"scripts": {
"dev": "next dev -p 3000",
"build": "next build",
"start": "next start",
"prisma:generate": "prisma generate",
"prisma:migrate": "prisma migrate dev"
},
"dependencies": {
"@prisma/client": "^5.15.1",
"bcryptjs": "^2.4.3",
"next": "14.2.4",
"next-auth": "^4.24.7",
"react": "18.2.0",
"react-dom": "18.2.0",
"zod": "^3.23.8"
},
"devDependencies": {
"autoprefixer": "^10.4.18",
"postcss": "^8.4.38",
"prisma": "^5.15.1",
"tailwindcss": "^3.4.4",
"typescript": "^5.4.5"
}
}

.env.example
env
For dev, SQLite is simplest
 
DATABASE_URL="file:./dev.db"

NextAuth
 
NEXTAUTH_URL="http://localhost:3000"
NEXTAUTH_SECRET="replace-with-a-strong-random-secret"

prisma/schema.prisma
prisma
generator client {
provider = "prisma-client-js"
}

datasource db {
provider = "sqlite"
url      = env("DATABASE_URL")
}

model User {
id                String   @id @default(cuid())
name              String?
email             String   @unique
passwordHash     String
isLawyerVerified  Boolean  @default(false)
barId             String?
barState          String?
city              String?
bio               String?
createdAt         DateTime @default(now())
updatedAt         DateTime @updatedAt
posts             Post[]
}

enum PostType {
ARTICLE
ISSUE
}

model Post {
id          String   @id @default(cuid())
title       String
content     String
type        PostType
city        String?
tags        String[]
authorId    String
author      User     @relation(fields: [authorId], references: [id])
createdAt   DateTime @default(now())
updatedAt   DateTime @updatedAt
status      String   @default("PUBLISHED") // For issues: OPEN, IN_PROGRESS, RESOLVED possible later
}

tailwind.config.js
js
/** @type {import('tailwindcss').Config} */
module.exports = {
content: ["./src/*/.{js,ts,jsx,tsx}"],
theme: {
extend: {
colors: {
navy: "#0E1A2B",
gold: "#C9A86A",
slate: "#6B7280"
}
}
},
plugins: []
};

postcss.config.js
js
module.exports = {
plugins: {
tailwindcss: {},
autoprefixer: {}
}
};

src/styles/globals.css
css
@tailwind base;
@tailwind components;
@tailwind utilities;

html, body { height: 100%; }
body { @apply bg-white text-slate; }
a { @apply text-navy hover:underline; }
.btn { @apply inline-flex items-center justify-center rounded-md px-4 py-2 font-medium transition-colors; }
.btn-primary { @apply bg-navy text-white hover:bg-black; }
.btn-secondary { @apply bg-gold text-navy hover:opacity-90; }
.card { @apply rounded-lg border border-gray-200 p-4 shadow-sm bg-white; }
.input { @apply w-full rounded-md border border-gray-300 px-3 py-2 focus:outline-none focus:ring-2 focus:ring-gold; }
.label { @apply text-sm font-medium text-navy; }

src/lib/prisma.ts
ts
import { PrismaClient } from "@prisma/client";

declare global {
var prisma: PrismaClient | undefined;
}

export const prisma = global.prisma ?? new PrismaClient();

if (process.env.NODE_ENV !== "production") global.prisma = prisma;

src/pages/_app.tsx
tsx
import "@/styles/globals.css";
import type { AppProps } from "next/app";
import { SessionProvider } from "next-auth/react";
import Layout from "@/components/Layout";

export default function App({ Component, pageProps: { session, ...pageProps } }: AppProps) {
return (
<SessionProvider session={session}>
<Layout>
<Component {...pageProps} />
</Layout>
</SessionProvider>
);
}

src/components/Layout.tsx
tsx
import Link from "next/link";
import { useSession, signIn, signOut } from "next-auth/react";
import React from "react";

export default function Layout({ children }: { children: React.ReactNode }) {
const { data: session } = useSession();

return (
<div className="min-h-screen flex flex-col">
<header className="border-b bg-white">
<div className="mx-auto max-w-6xl px-4 py-3 flex items-center justify-between">
<Link href="/" className="text-xl font-semibold text-navy">CivicLaw Voices</Link>
<nav className="flex gap-4 items-center">
<Link href="/articles" className="hover:underline">Articles</Link>
<Link href="/issues" className="hover:underline">City Issues</Link>
{session?.user ? (
<>
<Link href="/publish" className="btn btn-secondary">Publish</Link>
<Link href={/profile/${(session.user as any).id}} className="hover:underline">Profile</Link>
<button className="btn btn-primary" onClick={() => signOut()}>Sign out</button>
</>
) : (
<>
<Link href="/signup" className="btn btn-secondary">Join as Lawyer</Link>
<button className="btn btn-primary" onClick={() => signIn()}>Sign in</button>
</>
)}
</nav>
</div>
</header>
<main className="flex-1">
<div className="mx-auto max-w-6xl px-4 py-8">{children}</div>
</main>
<footer className="border-t">
<div className="mx-auto max-w-6xl px-4 py-6 text-sm text-gray-500">
© {new Date().getFullYear()} CivicLaw Voices • Built for verified lawyers and communities
</div>
</footer>
</div>
);
}

src/pages/index.tsx
tsx
import Link from "next/link";

export default function Home() {
return (
<div className="grid gap-10">
<section className="text-center py-16 bg-[linear-gradient(135deg,#0E1A2B,transparent)] rounded-xl text-white">
<h1 className="text-4xl md:text-5xl font-bold">Amplify Your Legal Voice</h1>
<p className="mt-4 text-lg opacity-90">Verified lawyers publish city issues and legal insights to inform and advocate.</p>
<div className="mt-8 flex justify-center gap-4">
<Link href="/signup" className="btn btn-secondary">Join as a Lawyer</Link>
<Link href="/articles" className="btn btn-primary bg-white text-navy hover:bg-gray-100">Explore Articles</Link>
</div>
</section>

<section className="grid md:grid-cols-2 gap-6">
<div className="card">
<h3 className="text-xl font-semibold text-navy">City Problem Hub</h3>
<p className="mt-2 text-gray-600">Report and track civic issues by location with legal context and solutions.</p>
<Link href="/issues" className="mt-4 inline-block text-navy underline">Browse City Issues →</Link>
</div>
<div className="card">
<h3 className="text-xl font-semibold text-navy">Articles Library</h3>
<p className="mt-2 text-gray-600">Read vetted legal insights by verified attorneys across jurisdictions.</p>
<Link href="/articles" className="mt-4 inline-block text-navy underline">Explore Articles →</Link>
</div>
</section>
</div>
);
}

src/pages/signup.tsx
tsx
import { FormEvent, useState } from "react";
import { signIn } from "next-auth/react";
import { useRouter } from "next/router";

export default function SignUp() {
const [form, setForm] = useState({ name: "", email: "", password: "" });
const [loading, setLoading] = useState(false);
const router = useRouter();

async function onSubmit(e: FormEvent) {
e.preventDefault();
setLoading(true);
const res = await fetch("/api/signup", {
method: "POST",
headers: { "Content-Type": "application/json" },
body: JSON.stringify(form)
});
setLoading(false);
if (res.ok) {
await signIn("credentials", { email: form.email, password: form.password, callbackUrl: "/verify" });
} else {
alert("Sign up failed");
}
}

return (
<div className="max-w-md mx-auto card">
<h1 className="text-2xl font-semibold text-navy">Create your account</h1>
<p className="text-sm text-gray-500 mt-1">Accounts must be verified to publish.</p>
<form className="mt-6 grid gap-4" onSubmit={onSubmit}>
<label className="grid gap-1">
<span className="label">Full name</span>
<input className="input" value={form.name} onChange={e => setForm({ ...form, name: e.target.value })} required />
</label>
<label className="grid gap-1">
<span className="label">Email</span>
<input type="email" className="input" value={form.email} onChange={e => setForm({ ...form, email: e.target.value })} required />
</label>
<label className="grid gap-1">
<span className="label">Password</span>
<input type="password" className="input" value={form.password} onChange={e => setForm({ ...form, password: e.target.value })} required />
</label>
<button className="btn btn-primary" disabled={loading}>{loading ? "Creating..." : "Sign up"}</button>
</form>
</div>
);
}

src/pages/verify.tsx
tsx
import { useState, FormEvent } from "react";
import { useSession } from "next-auth/react";
import { useRouter } from "next/router";

export default function Verify() {
const { data: session } = useSession();
const [form, setForm] = useState({ barId: "", barState: "", city: "", bio: "" });
const [loading, setLoading] = useState(false);
const router = useRouter();

async function onSubmit(e: FormEvent) {
e.preventDefault();
setLoading(true);
const res = await fetch("/api/verifyLawyer", {
method: "POST",
headers: { "Content-Type": "application/json" },
body: JSON.stringify(form)
});
setLoading(false);
if (res.ok) {
alert("Verification submitted. In this demo, valid patterns auto-verify.");
router.push("/publish");
} else {
const msg = await res.text();
alert(msg || "Verification failed");
}
}

return (
<div className="max-w-lg mx-auto card">
<h1 className="text-2xl font-semibold text-navy">Lawyer Verification</h1>
<p className="text-sm text-gray-500 mt-1">Provide your bar credentials. Demo auto-approves if Bar ID starts with LAW- and 5 digits (e.g., LAW-12345).</p>
{session ? (
<form className="mt-6 grid gap-4" onSubmit={onSubmit}>
<label className="grid gap-1">
<span className="label">Bar ID</span>
<input className="input" value={form.barId} onChange={e => setForm({ ...form, barId: e.target.value })} required />
</label>
<label className="grid gap-1">
<span className="label">Bar State</span>
<input className="input" value={form.barState} onChange={e => setForm({ ...form, barState: e.target.value })} required />
</label>
<label className="grid gap-1">
<span className="label">City</span>
<input className="input" value={form.city} onChange={e => setForm({ ...form, city: e.target.value })} />
</label>
<label className="grid gap-1">
<span className="label">Short Bio</span>
<textarea className="input" rows={4} value={form.bio} onChange={e => setForm({ ...form, bio: e.target.value })} />
</label>
<button className="btn btn-primary" disabled={loading}>{loading ? "Submitting..." : "Submit for Verification"}</button>
</form>
) : (
<p>Please sign in to verify.</p>
)}
</div>
);
}

src/pages/publish.tsx
tsx
import { GetServerSideProps } from "next";
import { getSession, useSession } from "next-auth/react";
import { useState, FormEvent } from "react";
import { prisma } from "@/lib/prisma";

export const getServerSideProps: GetServerSideProps = async (ctx) => {
const session = await getSession(ctx);
if (!session) return { redirect: { destination: "/api/auth/signin", permanent: false } };
const user = await prisma.user.findUnique({ where: { email: session.user?.email || "" } });
if (!user?.isLawyerVerified) {
return { redirect: { destination: "/verify", permanent: false } };
}
return { props: {} };
};

export default function Publish() {
const { data: session } = useSession();
const [form, setForm] = useState({ title: "", content: "", type: "ARTICLE", city: "", tags: "" });
const [loading, setLoading] = useState(false);

async function onSubmit(e: FormEvent) {
e.preventDefault();
setLoading(true);
const res = await fetch("/api/posts", {
method: "POST",
headers: { "Content-Type": "application/json" },
body: JSON.stringify({ ...form, tags: form.tags.split(",").map(t => t.trim()).filter(Boolean) })
});
setLoading(false);
if (res.ok) {
alert("Published!");
setForm({ title: "", content: "", type: "ARTICLE", city: "", tags: "" });
} else {
alert("Failed to publish");
}
}

return (
<div className="max-w-2xl mx-auto card">
<h1 className="text-2xl font-semibold text-navy">Publish</h1>
<form className="mt-6 grid gap-4" onSubmit={onSubmit}>
<label className="grid gap-1">
<span className="label">Post Type</span>
<select className="input" value={form.type} onChange={e => setForm({ ...form, type: e.target.value })}>
<option value="ARTICLE">Article</option>
<option value="ISSUE">City Issue</option>
</select>
</label>
<label className="grid gap-1">
<span className="label">Title</span>
<input className="input" value={form.title} onChange={e => setForm({ ...form, title: e.target.value })} required />
</label>
{form.type === "ISSUE" && (
<label className="grid gap-1">
<span className="label">City</span>
<input className="input" value={form.city} onChange={e => setForm({ ...form, city: e.target.value })} required />
</label>
)}
<label className="grid gap-1">
<span className="label">Tags (comma separated)</span>
<input className="input" value={form.tags} onChange={e => setForm({ ...form, tags: e.target.value })} />
</label>
<label className="grid gap-1">
<span className="label">Content</span>
<textarea className="input" rows={10} value={form.content} onChange={e => setForm({ ...form, content: e.target.value })} required />
</label>
<button className="btn btn-primary" disabled={loading}>{loading ? "Publishing..." : "Publish"}</button>
</form>
</div>
);
}

src/pages/articles/index.tsx
tsx
import { prisma } from "@/lib/prisma";
import { GetServerSideProps } from "next";
import Link from "next/link";

export const getServerSideProps: GetServerSideProps = async () => {
const posts = await prisma.post.findMany({
where: { type: "ARTICLE" },
orderBy: { createdAt: "desc" },
include: { author: true }
});
return { props: { posts: JSON.parse(JSON.stringify(posts)) } };
};

export default function Articles({ posts }: any) {
return (
<div className="grid gap-6">
<h1 className="text-3xl font-semibold text-navy">Articles</h1>
<div className="grid md:grid-cols-2 gap-6">
{posts.map((p: any) => (
<article key={p.id} className="card">
<h3 className="text-xl font-semibold">{p.title}</h3>
<p className="text-sm text-gray-500 mt-1">By {p.author?.name || "Unknown"} · {new Date(p.createdAt).toLocaleDateString()}</p>
<p className="mt-3 line-clamp-3 text-gray-700">{p.content}</p>
</article>
))}
</div>
</div>
);
}

src/pages/issues/index.tsx
tsx
import { prisma } from "@/lib/prisma";
import { GetServerSideProps } from "next";

export const getServerSideProps: GetServerSideProps = async () => {
const posts = await prisma.post.findMany({
where: { type: "ISSUE" },
orderBy: { createdAt: "desc" },
include: { author: true }
});
return { props: { posts: JSON.parse(JSON.stringify(posts)) } };
};

export default function Issues({ posts }: any) {
return (
<div className="grid gap-6">
<h1 className="text-3xl font-semibold text-navy">City Issues</h1>
<div className="grid gap-6">
{posts.map((p: any) => (
<article key={p.id} className="card">
<div className="flex items-center justify-between">
<h3 className="text-xl font-semibold">{p.title}</h3>
<span className="text-xs bg-gray-100 px-2 py-1 rounded">{p.city || "N/A"}</span>
</div>
<p className="text-sm text-gray-500 mt-1">By {p.author?.name || "Unknown"} · {new Date(p.createdAt).toLocaleDateString()}</p>
<p className="mt-3 text-gray-700">{p.content}</p>
</article>
))}
</div>
</div>
);
}

src/pages/profile/[id].tsx
tsx
import { GetServerSideProps } from "next";
import { prisma } from "@/lib/prisma";

export const getServerSideProps: GetServerSideProps = async ({ params }) => {
const id = params?.id as string;
const user = await prisma.user.findUnique({
where: { id },
include: { posts: { orderBy: { createdAt: "desc" } } }
});
if (!user) return { notFound: true };
return { props: { user: JSON.parse(JSON.stringify(user)) } };
};

export default function Profile({ user }: any) {
return (
<div className="grid gap-6">
<div className="card">
<div className="flex items-center justify-between">
<h1 className="text-3xl font-semibold text-navy">{user.name || "Lawyer"}</h1>
<span className={text-xs px-2 py-1 rounded ${user.isLawyerVerified ? "bg-green-100 text-green-700" : "bg-yellow-100 text-yellow-700"}}>
{user.isLawyerVerified ? "Verified Lawyer" : "Verification Pending"}
</span>
</div>
<p className="text-sm text-gray-600 mt-1">{user.city || ""}</p>
<p className="mt-3 text-gray-700">{user.bio || "No bio provided."}</p>
{user.barId && <p className="text-xs text-gray-500 mt-2">Bar ID: {user.barId} • {user.barState}</p>}
</div>

<section className="grid gap-4">
<h2 className="text-xl font-semibold text-navy">Posts</h2>
<div className="grid md:grid-cols-2 gap-6">
{user.posts.map((p: any) => (
<article key={p.id} className="card">
<div className="flex items-center justify-between">
<h3 className="text-lg font-semibold">{p.title}</h3>
<span className="text-xs bg-gray-100 px-2 py-1 rounded">{p.type}</span>
</div>
<p className="text-sm text-gray-500 mt-1">{new Date(p.createdAt).toLocaleDateString()}</p>
<p className="mt-2 line-clamp-3 text-gray-700">{p.content}</p>
</article>
))}
</div>
</section>
</div>
);
}

src/pages/api/auth/[...nextauth].ts
ts
import NextAuth from "next-auth";
import Credentials from "next-auth/providers/credentials";
import { prisma } from "@/lib/prisma";
import bcrypt from "bcryptjs";

export default NextAuth({
providers: [
Credentials({
name: "Credentials",
credentials: {
email: { label: "Email", type: "email" },
password: { label: "Password", type: "password" }
},
async authorize(credentials) {
if (!credentials?.email || !credentials?.password) return null;
const user = await prisma.user.findUnique({ where: { email: credentials.email } });
if (!user) return null;
const valid = await bcrypt.compare(credentials.password, user.passwordHash);
if (!valid) return null;
return { id: user.id, email: user.email, name: user.name };
}
})
],
session: { strategy: "jwt" },
pages: { signIn: "/api/auth/signin" },
callbacks: {
async jwt({ token, user }) {
if (user) token.id = (user as any).id;
return token;
},
async session({ session, token }) {
if (session.user && token) (session.user as any).id = token.id as string;
return session;
}
},
secret: process.env.NEXTAUTH_SECRET
});

src/pages/api/signup.ts
ts
import type { NextApiRequest, NextApiResponse } from "next";
import { prisma } from "@/lib/prisma";
import bcrypt from "bcryptjs";

export default async function handler(req: NextApiRequest, res: NextApiResponse) {
if (req.method !== "POST") return res.status(405).end();
const { name, email, password } = req.body || {};
if (!email || !password) return res.status(400).send("Missing fields");
const exists = await prisma.user.findUnique({ where: { email } });
if (exists) return res.status(400).send("Email already in use");
const passwordHash = await bcrypt.hash(password, 10);
await prisma.user.create({ data: { name: name || "", email, passwordHash } });
res.status(200).end();
}

src/pages/api/verifyLawyer.ts
ts
import type { NextApiRequest, NextApiResponse } from "next";
import { getServerSession } from "next-auth/next";
import authOptions from "./auth/[...nextauth]";
import { prisma } from "@/lib/prisma";

export default async function handler(req: NextApiRequest, res: NextApiResponse) {
if (req.method !== "POST") return res.status(405).end();
const session = await getServerSession(req, res, (authOptions as any).authOptions || (authOptions as any));
if (!session?.user?.email) return res.status(401).send("Unauthorized");

const { barId, barState, city, bio } = req.body || {};
if (!barId || !barState) return res.status(400).send("Missing bar info");

// Demo auto-verify rule: Bar ID like "LAW-12345"
const auto = /^LAW-\d{5}$/.test(barId);
const user = await prisma.user.update({
where: { email: session.user.email },
data: {
barId,
barState,
city: city || null,
bio: bio || null,
isLawyerVerified: auto
}
});

return res.status(200).json({ verified: user.isLawyerVerified });
}

src/pages/api/posts.ts
ts
import type { NextApiRequest, NextApiResponse } from "next";
import { getServerSession } from "next-auth/next";
import authOptions from "./auth/[...nextauth]";
import { prisma } from "@/lib/prisma";

export default async function handler(req: NextApiRequest, 