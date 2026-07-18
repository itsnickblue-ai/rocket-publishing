import { useState, useEffect, useCallback, useRef, useMemo } from 'react'
import { Rocket, BookOpen, Users, TrendingUp, Clock, Star, Menu, X, ChevronDown, Check, ArrowRight, Download, Image, Globe, DollarSign, Bell, LogOut, Plus, Search, Filter, SortAsc, SortDesc, Edit3, Upload, Palette, Layout as LayoutIcon, BarChart3, LineChart, Activity, BookMarked, Crown } from 'lucide-react'

const BASE = window.__BACKEND_URL__ || '';

async function apiFetch(path, opts = {}) {
  const BASE = window.__BACKEND_URL__ || '';
  for (let i = 0; i < 5; i++) {
    try {
      const r = await fetch(BASE + path, opts);
      if (r.ok) return r.json();
    } catch (_) {}
    await new Promise(r => setTimeout(r, 1500));
  }
  return null;
}

function LandingPage({ onGetStarted, onLogin, onSignup, onStore }) {
  const [menuOpen, setMenuOpen] = useState(false);

  useEffect(() => {
    const style = document.createElement('style');
    style.textContent = `

      * { margin: 0; padding: 0; box-sizing: border-box; }
      body { font-family: 'DM Sans', sans-serif; background: #0a0d18; color: #e6eaf2; }
      h1, h2, h3, h4, h5, h6 { font-family: 'Space Grotesk', sans-serif; }
    `;
    document.head.appendChild(style);
    return () => style.remove();
  }, []);

  return (
    <div className="bg-[#0a0f1e] min-h-screen">
      {/* Navbar */}
      <nav className="fixed top-0 left-0 right-0 z-50 bg-[#0a0d18]/90 backdrop-blur-lg border-b border-[#1E90FF]/20">
        <div className="max-w-7xl mx-auto px-4 sm:px-6 lg:px-8">
          <div className="flex items-center justify-between h-16">
            <div className="flex items-center gap-2">
              <div className="w-8 h-8 rounded-lg bg-gradient-to-br from-[#1E90FF] to-[#FF6B35] flex items-center justify-center">
                <Rocket className="w-5 h-5 text-white" />
              </div>
              <span className="text-xl font-bold font-heading text-white">Rocket Publishing</span>
            </div>
            <div className="hidden md:flex items-center gap-6">
              <a href="#features" className="text-sm text-gray-300 hover:text-[#1E90FF] transition-colors">Features</a>
              <a href="#services" className="text-sm text-gray-300 hover:text-[#1E90FF] transition-colors">Services</a>
              <button onClick={onStore} className="bg-[#FF6B35] hover:bg-[#e55a2b] text-white px-5 py-2 rounded-lg text-sm font-semibold transition-all duration-200 hover:shadow-lg hover:shadow-[#FF6B35]/25">
                Browse Store
              </button>
            </div>
            <button onClick={() => setMenuOpen(!menuOpen)} className="md:hidden text-white p-2">
              {menuOpen ? <X className="w-6 h-6" /> : <Menu className="w-6 h-6" />}
            </button>
          </div>
        </div>
        {menuOpen && (
          <div className="md:hidden bg-[#0a0d18] border-b border-[#1E90FF]/20 px-4 py-4 space-y-3">
            <a href="#features" className="block text-sm text-gray-300 hover:text-[#1E90FF] py-2" onClick={() => setMenuOpen(false)}>Features</a>
            <a href="#services" className="block text-sm text-gray-300 hover:text-[#1E90FF] py-2" onClick={() => setMenuOpen(false)}>Services</a>
            <button onClick={() => { onStore(); setMenuOpen(false); }} className="w-full bg-[#FF6B35] hover:bg-[#e55a2b] text-white px-5 py-3 rounded-lg text-sm font-semibold">Browse Store</button>
          </div>
        )}
      </nav>

      {/* Hero */}
      <section className="pt-28 pb-16 px-4">
        <div className="max-w-7xl mx-auto text-center">
          <div className="inline-flex items-center gap-2 bg-[#1E90FF]/10 border border-[#1E90FF]/30 rounded-full px-4 py-1.5 mb-6">
            <Rocket className="w-4 h-4 text-[#1E90FF]" />
            <span className="text-sm text-[#1E90FF] font-medium">Your book, published in 30 days</span>
          </div>
          <h1 className="text-4xl md:text-6xl lg:text-7xl font-bold text-white mb-6 leading-tight">
            From Manuscript to<br />
            <span className="text-transparent bg-clip-text bg-gradient-to-r from-[#1E90FF] to-[#FF6B35]">Market in 30 Days</span>
          </h1>
          <p className="text-lg md:text-xl text-gray-400 max-w-2xl mx-auto mb-10">
            Rocket Publishing offers professional services to help you publish your book — manuscript editing,
            cover design, formatting, distribution, and more. Browse our store and purchase exactly what you need.
          </p>
          <div className="flex flex-col sm:flex-row items-center justify-center gap-4">
            <button onClick={onStore} className="bg-[#FF6B35] hover:bg-[#e55a2b] text-white px-8 py-4 rounded-xl text-lg font-bold transition-all duration-200 hover:shadow-xl hover:shadow-[#FF6B35]/25 flex items-center gap-2">
              Browse Our Services <ArrowRight className="w-5 h-5" />
            </button>
          </div>
        </div>
      </section>

      {/* Stats */}
      <section className="py-12 px-4">
        <div className="max-w-6xl mx-auto grid grid-cols-1 md:grid-cols-3 gap-6">
          <div className="bg-[#0a0d18] border border-[#1E90FF]/20 rounded-2xl p-8 text-center hover:border-[#1E90FF]/40 transition-all duration-200">
            <Clock className="w-10 h-10 text-[#1E90FF] mx-auto mb-3" />
            <div className="text-4xl font-bold text-white font-heading">30 Days</div>
            <div className="text-gray-400 mt-1">Average time to publish</div>
          </div>
          <div className="bg-[#0a0d18] border border-[#1E90FF]/20 rounded-2xl p-8 text-center hover:border-[#1E90FF]/40 transition-all duration-200">
            <BookOpen className="w-10 h-10 text-[#1E90FF] mx-auto mb-3" />
            <div className="text-4xl font-bold text-white font-heading">10,000+</div>
            <div className="text-gray-400 mt-1">Books published</div>
          </div>
          <div className="bg-[#0a0d18] border border-[#1E90FF]/20 rounded-2xl p-8 text-center hover:border-[#1E90FF]/40 transition-all duration-200">
            <Star className="w-10 h-10 text-[#FF6B35] mx-auto mb-3" />
            <div className="text-4xl font-bold text-white font-heading">95%</div>
            <div className="text-gray-400 mt-1">Author satisfaction rate</div>
          </div>
        </div>
      </section>

      {/* Services */}
      <section id="services" className="py-20 px-4">
        <div className="max-w-7xl mx-auto">
          <h2 className="text-3xl md:text-4xl font-bold text-white text-center mb-4">Our Publishing Services</h2>
          <p className="text-gray-400 text-center max-w-2xl mx-auto mb-16 text-lg">
            Purchase exactly the services you need — no membership required. We handle every step of the publishing process.
          </p>
          <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-4 gap-6">
            <div className="bg-[#0a0d18] border border-[#1E90FF]/20 rounded-xl p-8 hover:border-[#1E90FF]/40 transition-all duration-200 group">
              <div className="w-12 h-12 rounded-xl bg-[#1E90FF]/10 flex items-center justify-center mb-5 group-hover:bg-[#1E90FF]/20 transition-colors">
                <Upload className="w-6 h-6 text-[#1E90FF]" />
              </div>
              <h3 className="text-xl font-bold text-white mb-3 font-heading">Manuscript Formatting</h3>
              <p className="text-gray-400 text-sm leading-relaxed">Upload your manuscript and we format it to industry standards. Purchase this service once — no subscription needed.</p>
              <button onClick={onStore} className="mt-4 text-[#1E90FF] text-sm font-semibold flex items-center gap-1 hover:underline">From $29 <ArrowRight className="w-3 h-3" /></button>
            </div>
            <div className="bg-[#0a0d18] border border-[#1E90FF]/20 rounded-xl p-8 hover:border-[#1E90FF]/40 transition-all duration-200 group">
              <div className="w-12 h-12 rounded-xl bg-[#FF6B35]/10 flex items-center justify-center mb-5 group-hover:bg-[#FF6B35]/20 transition-colors">
                <Palette className="w-6 h-6 text-[#FF6B35]" />
              </div>
              <h3 className="text-xl font-bold text-white mb-3 font-heading">Cover Design</h3>
              <p className="text-gray-400 text-sm leading-relaxed">Get a professional book cover designed by our team. Choose from our templates or request a custom design.</p>
              <button onClick={onStore} className="mt-4 text-[#FF6B35] text-sm font-semibold flex items-center gap-1 hover:underline">From $49 <ArrowRight className="w-3 h-3" /></button>
            </div>
            <div className="bg-[#0a0d18] border border-[#1E90FF]/20 rounded-xl p-8 hover:border-[#1E90FF]/40 transition-all duration-200 group">
              <div className="w-12 h-12 rounded-xl bg-[#1E90FF]/10 flex items-center justify-center mb-5 group-hover:bg-[#1E90FF]/20 transition-colors">
                <Globe className="w-6 h-6 text-[#1E90FF]" />
              </div>
              <h3 className="text-xl font-bold text-white mb-3 font-heading">Distribution Package</h3>
              <p className="text-gray-400 text-sm leading-relaxed">Distribute your book to Amazon, Barnes & Noble, Kobo, and more. One-time fee, lifetime distribution.</p>
              <button onClick={onStore} className="mt-4 text-[#1E90FF] text-sm font-semibold flex items-center gap-1 hover:underline">$99 <ArrowRight className="w-3 h-3" /></button>
            </div>
            <div className="bg-[#0a0d18] border border-[#1E90FF]/20 rounded-xl p-8 hover:border-[#1E90FF]/40 transition-all duration-200 group">
              <div className="w-12 h-12 rounded-xl bg-[#FF6B35]/10 flex items-center justify-center mb-5 group-hover:bg-[#FF6B35]/20 transition-colors">
                <Edit3 className="w-6 h-6 text-[#FF6B35]" />
              </div>
              <h3 className="text-xl font-bold text-white mb-3 font-heading">Editing & Proofreading</h3>
              <p className="text-gray-400 text-sm leading-relaxed">Professional editing services to polish your manuscript. Developmental editing, copyediting, and proofreading.</p>
              <button onClick={onStore} className="mt-4 text-[#FF6B35] text-sm font-semibold flex items-center gap-1 hover:underline">From $199 <ArrowRight className="w-3 h-3" /></button>
            </div>
          </div>
        </div>
      </section>

      {/* Testimonials */}
      <section className="py-16 px-4">
        <div className="max-w-6xl mx-auto">
          <h2 className="text-3xl md:text-4xl font-bold text-white text-center mb-4">Trusted by Thousands of Authors</h2>
          <p className="text-gray-400 text-center mb-12">Join the 10,000+ authors who've published with Rocket Publishing.</p>
          <div className="grid grid-cols-1 md:grid-cols-3 gap-6">
            <div className="bg-[#0a0d18] border border-[#1E90FF]/20 rounded-xl p-6">
              <div className="flex items-center gap-1 mb-4">
                {[...Array(5)].map((_, i) => <Star key={i} className="w-4 h-4 text-[#FF6B35] fill-current" />)}
              </div>
              <p className="text-gray-300 mb-4 italic">"I had my manuscript formatted and ready for print in just two days. The cover generator is incredible — I got a professional cover without spending thousands."</p>
              <div className="flex items-center gap-3">
                <div className="w-10 h-10 rounded-full bg-[#1E90FF]/20 flex items-center justify-center text-[#1E90FF] font-bold">SP</div>
                <div>
                  <p className="text-white text-sm font-semibold">Sarah Patel</p>
                  <p className="text-gray-500 text-xs">Author of "The Last Lighthouse"</p>
                </div>
              </div>
            </div>
            <div className="bg-[#0a0d18] border border-[#1E90FF]/20 rounded-xl p-6">
              <div className="flex items-center gap-1 mb-4">
                {[...Array(5)].map((_, i) => <Star key={i} className="w-4 h-4 text-[#FF6B35] fill-current" />)}
              </div>
              <p className="text-gray-300 mb-4 italic">"Distribution was a breeze. My book is now available on Amazon, Barnes & Noble, and Kobo. The dashboard makes it easy to track sales across all platforms."</p>
              <div className="flex items-center gap-3">
                <div className="w-10 h-10 rounded-full bg-[#FF6B35]/20 flex items-center justify-center text-[#FF6B35] font-bold">MJ</div>
                <div>
                  <p className="text-white text-sm font-semibold">Marcus Johnson</p>
                  <p className="text-gray-500 text-xs">Self-published author, 5 books</p>
                </div>
              </div>
            </div>
            <div className="bg-[#0a0d18] border border-[#1E90FF]/20 rounded-xl p-6">
              <div className="flex items-center gap-1 mb-4">
                {[...Array(5)].map((_, i) => <Star key={i} className="w-4 h-4 text-[#FF6B35] fill-current" />)}
              </div>
              <p className="text-gray-300 mb-4 italic">"The 30-day publishing guarantee is real. From upload to available on Amazon in just 27 days. Rocket Publishing is a game-changer for indie authors."</p>
              <div className="flex items-center gap-3">
                <div className="w-10 h-10 rounded-full bg-[#1E90FF]/20 flex items-center justify-center text-[#1E90FF] font-bold">AL</div>
                <div>
                  <p className="text-white text-sm font-semibold">Aiko Tanaka</p>
                  <p className="text-gray-500 text-xs">Bestselling indie author</p>
                </div>
              </div>
            </div>
          </div>
        </div>
      </section>

      {/* Store CTA */}
      <section id="store" className="py-20 px-4">
        <div className="max-w-4xl mx-auto text-center">
          <div className="inline-flex items-center gap-2 bg-[#FF6B35]/10 border border-[#FF6B35]/30 rounded-full px-4 py-1.5 mb-6">
            <DollarSign className="w-4 h-4 text-[#FF6B35]" />
            <span className="text-sm text-[#FF6B35] font-medium">Pay per service — no subscription required</span>
          </div>
          <h2 className="text-3xl md:text-4xl font-bold text-white mb-4">Purchase What You Need, When You Need It</h2>
          <p className="text-gray-400 max-w-2xl mx-auto mb-10 text-lg">
            No memberships. No monthly fees. Just professional publishing services that you buy once and own.
          </p>
          <button onClick={onStore} className="bg-[#FF6B35] hover:bg-[#e55a2b] text-white px-8 py-4 rounded-xl text-lg font-bold transition-all duration-200 hover:shadow-xl hover:shadow-[#FF6B35]/25 flex items-center gap-2 mx-auto">
            Browse the Store <ArrowRight className="w-5 h-5" />
          </button>
        </div>
      </section>

      {/* Footer */}
      <footer className="border-t border-[#1E90FF]/20 py-12 px-4">
        <div className="max-w-7xl mx-auto">
          <div className="flex flex-col md:flex-row items-center justify-between gap-6">
            <div className="flex items-center gap-2">
              <div className="w-8 h-8 rounded-lg bg-gradient-to-br from-[#1E90FF] to-[#FF6B35] flex items-center justify-center">
                <Rocket className="w-5 h-5 text-white" />
              </div>
              <span className="text-xl font-bold text-white font-heading">Rocket Publishing</span>
            </div>
            <div className="flex items-center gap-6">
              <a href="#features" className="text-sm text-gray-400 hover:text-[#1E90FF] transition-colors">Features</a>
              <a href="#services" className="text-sm text-gray-400 hover:text-[#1E90FF] transition-colors">Services</a>
              <a href="#store" className="text-sm text-gray-400 hover:text-[#1E90FF] transition-colors">Store</a>
              <span className="text-sm text-gray-500">© 2025 Rocket Publishing</span>
            </div>
          </div>
        </div>
      </footer>
    </div>
  );
}

function ProductApp({ user, onLogout }) {
  /* NC_PLACEHOLDER_DASHBOARD — replaced by the real dashboard in Phase 2 */
  return (
    <div style={{ minHeight: '100vh', background: '#0a0d18', color: '#e6eaf2', display: 'flex', flexDirection: 'column', alignItems: 'center', justifyContent: 'center', gap: 16, padding: 24, textAlign: 'center' }}>
      <h1 style={{ fontSize: 28, fontWeight: 800, margin: 0 }}>Welcome, {user?.name || user?.email || 'there'} 👋</h1>
      <p style={{ color: '#9aa6bd', maxWidth: 460, lineHeight: 1.5, margin: 0 }}>Your account is ready. Your dashboard is being set up and will appear here shortly.</p>
      <button onClick={onLogout} style={{ marginTop: 8, padding: '10px 18px', borderRadius: 10, border: '1px solid #2a3350', background: 'transparent', color: '#e6eaf2', fontWeight: 600, cursor: 'pointer' }}>Log out</button>
    </div>
  );
}

function AuthGate({ onAuth, onClose }) {
  const [mode, setMode] = useState('signup');
  const [form, setForm] = useState({ name: '', email: '', password: '' });
  const [loading, setLoading] = useState(false);
  const [error, setError] = useState('');
  const _ip = { width: '100%', padding: '11px 13px', margin: '6px 0', borderRadius: 9, border: '1px solid #2a3350', background: '#0b1020', color: '#e6eaf2', fontSize: 14, outline: 'none', boxSizing: 'border-box' };
  const submit = async (e) => {
    e.preventDefault();
    if (!form.email || !form.password) return;
    setLoading(true); setError('');
    const _b = window.__NC_BASE__ || ''; const _s = window.__COMPANY_SLUG__ || '';
    const body = JSON.stringify({ email: form.email, password: form.password, name: form.name });
    const _call = () => fetch(`${_b}/api/c/${_s}/auth/${mode}`, { method: 'POST', headers: { 'Content-Type': 'application/json' }, body });
    try {
      let res; try { res = await _call(); } catch { await new Promise(r => setTimeout(r, 2500)); res = await _call(); }
      const json = await res.json();
      if (!json.ok) { setError(json.error || 'Authentication failed — please try again'); setLoading(false); return; }
      onAuth(json);
    } catch { setError('Connection error — please try again in a moment.'); setLoading(false); }
  };
  return (
    <div onClick={onClose} style={{ position: 'fixed', inset: 0, background: 'rgba(2,6,18,.7)', backdropFilter: 'blur(4px)', display: 'flex', alignItems: 'center', justifyContent: 'center', zIndex: 1000 }}>
      <form onClick={(e) => e.stopPropagation()} onSubmit={submit} style={{ background: '#0f1424', border: '1px solid #232b45', padding: 28, borderRadius: 16, width: 360, maxWidth: '90vw', color: '#e6eaf2' }}>
        <h3 style={{ margin: '0 0 16px', fontSize: 20, fontWeight: 700 }}>{mode === 'signup' ? 'Create your account' : 'Welcome back'}</h3>
        {mode === 'signup' && <input value={form.name} onChange={(e) => setForm({ ...form, name: e.target.value })} placeholder="Your name" style={_ip} />}
        <input value={form.email} onChange={(e) => setForm({ ...form, email: e.target.value })} placeholder="Work email" type="email" required style={_ip} />
        <input value={form.password} onChange={(e) => setForm({ ...form, password: e.target.value })} placeholder="Password (min 6 chars)" type="password" required style={_ip} />
        {error && <p style={{ color: '#f87171', fontSize: 13, margin: '6px 0 0' }}>{error}</p>}
        <button type="submit" disabled={loading} style={{ width: '100%', marginTop: 10, padding: '12px', borderRadius: 9, border: 'none', background: loading ? '#4b50b8' : '#6366f1', color: '#fff', fontWeight: 700, fontSize: 15, cursor: loading ? 'default' : 'pointer' }}>
          {loading ? '…' : mode === 'signup' ? 'Get started free' : 'Log in'}
        </button>
        <p onClick={() => { setMode(mode === 'signup' ? 'login' : 'signup'); setError(''); }} style={{ marginTop: 14, fontSize: 13, color: '#9aa6bd', cursor: 'pointer', textAlign: 'center' }}>
          {mode === 'signup' ? 'Already have an account? Log in' : 'New here? Create an account'}
        </p>
      </form>
    </div>
  );
}

function App() {
  const [auth, setAuth] = useState(() => {
    try {
      if (localStorage.getItem('nc_user') && !localStorage.getItem('nc_auth')) localStorage.removeItem('nc_user');
      const a = JSON.parse(localStorage.getItem('nc_auth') || 'null');
      return (a && a.token && a.user && typeof a.user.email === 'string') ? a : null;
    } catch { return null; }
  });
  const [showAuth, setShowAuth] = useState(false);
  useEffect(() => {
    if (!auth?.token) return;
    const _b = window.__NC_BASE__ || ''; const _s = window.__COMPANY_SLUG__ || '';
    fetch(`${_b}/api/c/${_s}/auth/me`, { headers: { Authorization: `Bearer ${auth.token}` } })
      .then(r => r.json()).then(d => { if (!d.ok) { localStorage.removeItem('nc_auth'); setAuth(null); } }).catch(() => {});
  }, []);
  const onAuth = (data) => { localStorage.setItem('nc_auth', JSON.stringify(data)); setAuth(data); setShowAuth(false); };
  const onLogout = () => { localStorage.removeItem('nc_auth'); setAuth(null); };
  if (auth?.user) return <ProductApp user={auth.user} token={auth.token} onLogout={onLogout} />;
  return (
    <>
      <LandingPage onGetStarted={() => setShowAuth(true)} onSignup={() => setShowAuth(true)} onLogin={() => setShowAuth(true)} onStore={() => {}} />
      {/* Fallback entry point (bottom-right so it never overlaps the nav) — guarantees a
          working login even if the landing's own buttons aren't wired to the auth modal. */}
      <button onClick={() => setShowAuth(true)} style={{ position: 'fixed', bottom: 20, right: 20, zIndex: 999, background: '#6366f1', color: '#fff', border: 'none', padding: '10px 18px', borderRadius: 999, fontWeight: 600, fontSize: 14, cursor: 'pointer', boxShadow: '0 6px 20px rgba(99,102,241,.45)' }}>Sign in</button>
      {showAuth && <AuthGate onAuth={onAuth} onClose={() => setShowAuth(false)} />}
    </>
  );
}

export default App;
