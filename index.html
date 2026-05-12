'use client'

import { useState, useEffect } from 'react'
import {
  MessageCircle,
  Trash2,
  Edit2,
  DollarSign,
  LogOut,
  Plus,
  Bell,
  Calendar,
  AlertCircle,
  TrendingUp,
  Clock,
  CheckCircle2,
  Settings,
} from 'lucide-react'
import { createClient } from '@supabase/supabase-js'
import Anthropic from '@anthropic-ai/sdk'

// ============ CONFIG ============
const supabaseUrl = process.env.NEXT_PUBLIC_SUPABASE_URL!
const supabaseKey = process.env.NEXT_PUBLIC_SUPABASE_ANON_KEY!
const supabase = createClient(supabaseUrl, supabaseKey)

const anthropic = new Anthropic({
  apiKey: process.env.ANTHROPIC_API_KEY,
})

const PROYECTOS = [
  { nombre: 'Los Sauces', bono: 52250, inicial: 3000, desc: 2000 },
  { nombre: 'Villa Norte', bono: 62900, inicial: 5000, desc: 3000 },
  { nombre: 'Sol de Ica', bono: 35500, inicial: 2500, desc: 1500 },
  { nombre: 'Villa Zafiro', bono: 52250, inicial: 3000, desc: 2000 },
]

const LOTES: Record<string, any[]> = {
  'Los Sauces': [
    { id: 'A-01', tipo: 'Frente a parque', area: 60, precio: 125000 },
    { id: 'A-02', tipo: 'Frente a parque', area: 60, precio: 125000 },
    { id: 'B-01', tipo: 'Pasaje', area: 55, precio: 110000 },
    { id: 'B-02', tipo: 'Esquina', area: 72, precio: 148000 },
  ],
  'Villa Norte': [
    { id: 'C-01', tipo: 'Frente a parque', area: 72, precio: 149000 },
    { id: 'C-02', tipo: 'Esquina', area: 80, precio: 165000 },
    { id: 'D-01', tipo: 'Pasaje', area: 60, precio: 122250 },
  ],
  'Sol de Ica': [
    { id: 'E-01', tipo: 'Frente a parque', area: 48, precio: 89500 },
    { id: 'E-02', tipo: 'Esquina', area: 58, precio: 107000 },
  ],
  'Villa Zafiro': [
    { id: 'F-01', tipo: 'Frente a parque', area: 60, precio: 122250 },
    { id: 'F-02', tipo: 'Esquina', area: 70, precio: 142000 },
  ],
}

// ETAPAS DEL LEAD
const ETAPAS = [
  { id: 'nuevo', label: 'Nuevo', color: 'bg-blue-100 text-blue-800', emoji: '🆕' },
  { id: 'contactado', label: 'Contactado', color: 'bg-yellow-100 text-yellow-800', emoji: '📞' },
  {
    id: 'interesado',
    label: 'Interesado',
    color: 'bg-orange-100 text-orange-800',
    emoji: '👀',
  },
  {
    id: 'negociando',
    label: 'Negociando',
    color: 'bg-purple-100 text-purple-800',
    emoji: '💬',
  },
  { id: 'cierre', label: 'Separación', color: 'bg-green-100 text-green-800', emoji: '✅' },
  { id: 'perdido', label: 'No Interesado', color: 'bg-red-100 text-red-800', emoji: '❌' },
]

// ============ MAIN COMPONENT ============
export default function App() {
  // STATE
  const [page, setPage] = useState('login')
  const [user, setUser] = useState<any>(null)
  const [leads, setLeads] = useState<any[]>([])
  const [showForm, setShowForm] = useState(false)
  const [editingLead, setEditingLead] = useState<any>(null)
  const [cotizacion, setCotizacion] = useState<any>(null)
  const [search, setSearch] = useState('')
  const [loading, setLoading] = useState(false)
  const [filterEtapa, setFilterEtapa] = useState('todos')
  const [sortBy, setSortBy] = useState('fecha')
  const [showSettings, setShowSettings] = useState(false)

  const [formData, setFormData] = useState({
    nombre: '',
    dni: '',
    tel: '',
    email: '',
    proyecto: 'Los Sauces',
    lote_id: '',
    ingresos: '',
    tiene_propiedad: false,
    etapa: 'nuevo',
    fecha_seguimiento: new Date().toISOString().split('T')[0],
    notas: '',
  })

  // CARGAR DATOS AL MONTAR
  useEffect(() => {
    const userStr = localStorage.getItem('user')
    if (userStr) {
      const u = JSON.parse(userStr)
      setUser(u)
      setPage('dashboard')
      cargarLeads(u.id)
    }
  }, [])

  // ============ FUNCIONES PRINCIPALES ============

  const cargarLeads = async (userId: string) => {
    try {
      const { data, error } = await supabase
        .from('leads')
        .select('*')
        .eq('asesor_id', userId)
        .order('fecha_creacion', { ascending: false })

      if (error) throw error
      setLeads(data || [])
    } catch (err) {
      console.error('Error:', err)
    }
  }

  const login = async (email: string, password: string) => {
    setLoading(true)
    try {
      // DEMO para desarrollo
      if (email === 'carlos@propia.pe' && password === 'carlos123') {
        const userData = {
          id: 'demo-user-' + Date.now(),
          nombre: 'Carlos Mendoza',
          email,
          rol: 'agente',
        }
        localStorage.setItem('user', JSON.stringify(userData))
        setUser(userData)
        setPage('dashboard')
        cargarLeads(userData.id)
      } else {
        alert('Email o contraseña incorrectos.\nDemo: carlos@propia.pe / carlos123')
      }
    } finally {
      setLoading(false)
    }
  }

  const guardarLead = async () => {
    if (!formData.nombre || !formData.dni) {
      alert('Nombre y DNI son obligatorios')
      return
    }

    setLoading(true)
    try {
      if (editingLead) {
        // ACTUALIZAR
        const { error } = await supabase
          .from('leads')
          .update({
            ...formData,
            fecha_actualizado: new Date().toISOString(),
          })
          .eq('id', editingLead.id)

        if (error) throw error
      } else {
        // CREAR
        const { error } = await supabase
          .from('leads')
          .insert({
            ...formData,
            asesor_id: user.id,
            fecha_creacion: new Date().toISOString(),
          })

        if (error) throw error
      }

      await cargarLeads(user.id)
      setShowForm(false)
      setEditingLead(null)
      setFormData({
        nombre: '',
        dni: '',
        tel: '',
        email: '',
        proyecto: 'Los Sauces',
        lote_id: '',
        ingresos: '',
        tiene_propiedad: false,
        etapa: 'nuevo',
        fecha_seguimiento: new Date().toISOString().split('T')[0],
        notas: '',
      })
    } catch (err) {
      console.error('Error:', err)
      alert('Error guardando')
    } finally {
      setLoading(false)
    }
  }

  const eliminarLead = async (id: string) => {
    if (!confirm('¿Eliminar este lead?')) return

    try {
      const { error } = await supabase.from('leads').delete().eq('id', id)
      if (error) throw error
      await cargarLeads(user.id)
    } catch (err) {
      console.error('Error:', err)
    }
  }

  const enviarWhatsApp = (lead: any) => {
    if (!lead.tel) {
      alert('Sin teléfono registrado')
      return
    }
    const msg = `Hola ${lead.nombre}, soy ${user.nombre}, tu asesor de Techo Propio. ¿Tienes un momento para hablar?`
    window.open(
      `https://wa.me/${lead.tel.replace(/\D/g, '')}?text=${encodeURIComponent(msg)}`,
      '_blank'
    )
  }

  const generarCotizacion = async (lead: any) => {
    const proyecto = PROYECTOS.find((p) => p.nombre === lead.proyecto)
    const lote = LOTES[lead.proyecto]?.[0]

    if (!proyecto || !lote) {
      alert('Datos incompletos')
      return
    }

    setLoading(true)
    try {
      const precio = lote.precio
      const bono = proyecto.bono
      const inicial = proyecto.inicial
      const desc = proyecto.desc
      const saldo = precio - bono - desc - inicial
      const cuota = saldo / 42

      const data = {
        proyecto: proyecto.nombre,
        loteId: lote.id,
        tipo: lote.tipo,
        area: lote.area,
        precio,
        bono,
        descTotal: desc,
        inicialCliente: inicial,
        saldoFinanciar: saldo,
        cuotaRegular: cuota,
      }

      // LLAMAR A CLAUDE
      const message = await anthropic.messages.create({
        model: 'claude-3-5-sonnet-20241022',
        max_tokens: 300,
        messages: [
          {
            role: 'user',
            content: `Eres asesor de Techo Propio Perú especializado en cerrar ventas.
Cliente: ${lead.nombre}, ingresos: S/ ${lead.ingresos}

COTIZACIÓN:
Proyecto: ${data.proyecto}
Lote: ${data.loteId} (${data.tipo}, ${data.area}m²)
Precio: S/ ${data.precio.toLocaleString()}
Bono TP: S/ ${data.bono.toLocaleString()}
CUOTA MENSUAL: S/ ${data.cuotaRegular.toFixed(2)} (42 meses)

Proporciona BREVEMENTE:
1. El argumento de venta MÁS FUERTE para este cliente
2. El próximo paso exacto a seguir
Sé conciso y enfocado en la venta.`,
          },
        ],
      })

      const analisis =
        message.content[0].type === 'text' ? message.content[0].text : ''

      setCotizacion({ lead, data, analisis })
    } catch (err) {
      console.error('Error:', err)
      alert('Error generando cotización')
    } finally {
      setLoading(false)
    }
  }

  const enviarCotizacionWhatsApp = () => {
    if (!cotizacion.lead.tel) {
      alert('Sin teléfono')
      return
    }

    const msg = `¡Hola ${cotizacion.lead.nombre}! 👋

Aquí está tu cotización del proyecto ${cotizacion.data.proyecto}:

📍 LOTE: ${cotizacion.data.loteId} (${cotizacion.data.tipo})
📏 ÁREA: ${cotizacion.data.area}m²
💰 PRECIO: S/ ${cotizacion.data.precio.toLocaleString()}

DESGLOSE:
✓ Bono TP: S/ ${cotizacion.data.bono.toLocaleString()}
✓ Descuento: S/ ${cotizacion.data.descTotal.toLocaleString()}
✓ Inicial: S/ ${cotizacion.data.inicialCliente.toLocaleString()}

📊 RESULTADO:
Cuota mensual: S/ ${cotizacion.data.cuotaRegular.toFixed(2)}
Plazo: 42 meses (sin intereses)

¿Te interesa? Conversemos. 📞`

    window.open(
      `https://wa.me/${cotizacion.lead.tel.replace(/\D/g, '')}?text=${encodeURIComponent(msg)}`,
      '_blank'
    )
  }

  // ============ ALERTAS Y RECORDATORIOS ============

  const getAlertas = () => {
    const hoy = new Date()
    hoy.setHours(0, 0, 0, 0)

    return [
      // Leads sin contactar hace más de 7 días
      ...leads.filter((l) => {
        if (!l.fecha_ultimo_contacto) return true
        const dias = Math.floor(
          (hoy - new Date(l.fecha_ultimo_contacto)) / (1000 * 60 * 60 * 24)
        )
        return dias > 7 && l.etapa !== 'perdido' && l.etapa !== 'cierre'
      }),
    ]
  }

  const getSeguimientosHoy = () => {
    const hoy = new Date().toISOString().split('T')[0]
    return leads.filter((l) => l.fecha_seguimiento === hoy && l.etapa !== 'cierre')
  }

  // ============ ESTADÍSTICAS ============

  const stats = {
    total: leads.length,
    nuevos: leads.filter((l) => l.etapa === 'nuevo').length,
    negociando: leads.filter((l) => l.etapa === 'negociando').length,
    cerrados: leads.filter((l) => l.etapa === 'cierre').length,
    calificados: leads.filter((l) => l.ingresos && l.ingresos <= 3626 && !l.tiene_propiedad)
      .length,
    tasa_cierre: leads.length
      ? Math.round((leads.filter((l) => l.etapa === 'cierre').length / leads.length) * 100)
      : 0,
  }

  const alertas = getAlertas()
  const seguimientosHoy = getSeguimientosHoy()

  // ============ FILTRADO Y ORDENAMIENTO ============

  let leadsFiltrados = leads

  // FILTRAR POR ETAPA
  if (filterEtapa !== 'todos') {
    leadsFiltrados = leadsFiltrados.filter((l) => l.etapa === filterEtapa)
  }

  // FILTRAR POR BÚSQUEDA
  if (search) {
    leadsFiltrados = leadsFiltrados.filter(
      (l) =>
        l.nombre.toLowerCase().includes(search.toLowerCase()) || l.dni.includes(search)
    )
  }

  // ORDENAR
  if (sortBy === 'fecha') {
    leadsFiltrados.sort((a, b) => new Date(b.fecha_creacion) - new Date(a.fecha_creacion))
  } else if (sortBy === 'proximo-seguimiento') {
    leadsFiltrados.sort(
      (a, b) =>
        new Date(a.fecha_seguimiento || '2099-12-31') -
        new Date(b.fecha_seguimiento || '2099-12-31')
    )
  } else if (sortBy === 'etapa') {
    const etapaOrder = { nuevo: 0, contactado: 1, interesado: 2, negociando: 3, cierre: 4, perdido: 5 }
    leadsFiltrados.sort((a, b) => (etapaOrder[a.etapa] || 0) - (etapaOrder[b.etapa] || 0))
  }

  // ============ RENDER: LOGIN ============

  if (page === 'login') {
    return (
      <div className="min-h-screen bg-gradient-to-br from-blue-600 to-blue-800 flex items-center justify-center p-4">
        <div className="bg-white rounded-xl shadow-2xl p-8 w-full max-w-md">
          <div className="text-center mb-8">
            <h1 className="text-5xl font-bold text-blue-600 mb-2">PropIA</h1>
            <p className="text-gray-600 text-lg font-semibold">Gestor Inteligente de Leads</p>
            <p className="text-gray-500 text-sm mt-2">Para asesores inmobiliarios de Techo Propio</p>
          </div>

          <form
            onSubmit={(e) => {
              e.preventDefault()
              const email = (document.getElementById('email') as any).value
              const password = (document.getElementById('password') as any).value
              login(email, password)
            }}
            className="space-y-4 mb-6"
          >
            <div>
              <label className="block text-sm font-semibold text-gray-700 mb-2">
                Email
              </label>
              <input
                id="email"
                type="email"
                defaultValue="carlos@propia.pe"
                className="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
              />
            </div>

            <div>
              <label className="block text-sm font-semibold text-gray-700 mb-2">
                Contraseña
              </label>
              <input
                id="password"
                type="password"
                defaultValue="carlos123"
                className="w-full px-4 py-2 border border-gray-300 rounded-lg focus:outline-none focus:ring-2 focus:ring-blue-500"
              />
            </div>

            <button
              type="submit"
              disabled={loading}
              className="w-full bg-blue-600 text-white py-3 rounded-lg hover:bg-blue-700 disabled:opacity-50 font-bold text-lg transition"
            >
              {loading ? '⏳ Ingresando...' : '🚀 Ingresar'}
            </button>
          </form>

          <div className="bg-blue-50 border border-blue-200 rounded-lg p-4">
            <p className="text-sm text-gray-700 font-semibold mb-2">🔑 Demo:</p>
            <p className="text-sm text-gray-600 mb-1">
              <code className="bg-white px-2 py-1 rounded border border-gray-200">
                carlos@propia.pe
              </code>
            </p>
            <p className="text-sm text-gray-600">
              <code className="bg-white px-2 py-1 rounded border border-gray-200">
                carlos123
              </code>
            </p>
          </div>

          <div className="mt-6 pt-6 border-t border-gray-200">
            <p className="text-xs text-gray-500 text-center">
              PropIA - Sistema SaaS individual para asesores 📈
            </p>
          </div>
        </div>
      </div>
    )
  }

  // ============ RENDER: DASHBOARD ============

  return (
    <div className="min-h-screen bg-gray-900 text-white">
      {/* NAVBAR */}
      <nav className="bg-gray-800 border-b border-gray-700 sticky top-0 z-40">
        <div className="max-w-7xl mx-auto px-4 py-4 flex justify-between items-center">
          <div>
            <h1 className="text-3xl font-bold text-blue-400">📊 PropIA</h1>
            <p className="text-sm text-gray-400">{user?.nombre}</p>
          </div>

          <div className="flex items-center gap-4">
            <div className="text-right">
              <p className="font-semibold">{user?.nombre}</p>
              <p className="text-xs text-gray-400">SaaS Individual</p>
            </div>

            <button
              onClick={() => setShowSettings(!showSettings)}
              className="p-2 hover:bg-gray-700 rounded-lg transition"
              title="Configuración"
            >
              <Settings size={20} />
            </button>

            <button
              onClick={() => {
                localStorage.clear()
                setPage('login')
                setUser(null)
                setLeads([])
              }}
              className="flex items-center gap-2 px-4 py-2 bg-red-600 hover:bg-red-700 rounded-lg transition font-semibold"
            >
              <LogOut size={18} />
              Salir
            </button>
          </div>
        </div>
      </nav>

      {/* ALERTAS URGENTES */}
      {alertas.length > 0 && (
        <div className="bg-red-900 border-b border-red-700 px-4 py-3">
          <div className="max-w-7xl mx-auto">
            <div className="flex items-center gap-2 text-red-200">
              <AlertCircle size={20} />
              <p className="font-semibold">
                ⚠️ {alertas.length} lead{alertas.length > 1 ? 's' : ''} sin contactar hace +7 días
              </p>
            </div>
            <p className="text-xs text-red-300 mt-1">
              {alertas.map((l) => l.nombre).join(', ')}
            </p>
          </div>
        </div>
      )}

      {/* SEGUIMIENTOS HOY */}
      {seguimientosHoy.length > 0 && (
        <div className="bg-blue-900 border-b border-blue-700 px-4 py-3">
          <div className="max-w-7xl mx-auto">
            <div className="flex items-center gap-2 text-blue-200">
              <Calendar size={20} />
              <p className="font-semibold">
                📅 {seguimientosHoy.length} seguimiento{seguimientosHoy.length > 1 ? 's' : ''} para
                hoy
              </p>
            </div>
            <p className="text-xs text-blue-300 mt-1">
              {seguimientosHoy.map((l) => l.nombre).join(', ')}
            </p>
          </div>
        </div>
      )}

      {/* MAIN CONTENT */}
      <main className="max-w-7xl mx-auto px-4 py-8">
        {/* STATS */}
        <div className="grid grid-cols-2 md:grid-cols-6 gap-4 mb-8">
          <div className="bg-gray-800 border border-gray-700 rounded-lg p-4">
            <p className="text-gray-400 text-xs font-semibold">Total</p>
            <p className="text-4xl font-bold text-blue-400 mt-1">{stats.total}</p>
            <p className="text-xs text-gray-500 mt-2">Leads registrados</p>
          </div>

          <div className="bg-gray-800 border border-gray-700 rounded-lg p-4">
            <p className="text-gray-400 text-xs font-semibold">Nuevos</p>
            <p className="text-4xl font-bold text-yellow-400 mt-1">{stats.nuevos}</p>
            <p className="text-xs text-gray-500 mt-2">Por contactar</p>
          </div>

          <div className="bg-gray-800 border border-gray-700 rounded-lg p-4">
            <p className="text-gray-400 text-xs font-semibold">Negociando</p>
            <p className="text-4xl font-bold text-purple-400 mt-1">{stats.negociando}</p>
            <p className="text-xs text-gray-500 mt-2">En proceso</p>
          </div>

          <div className="bg-gray-800 border border-gray-700 rounded-lg p-4">
            <p className="text-gray-400 text-xs font-semibold">Cerrados</p>
            <p className="text-4xl font-bold text-green-400 mt-1">{stats.cerrados}</p>
            <p className="text-xs text-gray-500 mt-2">Separaciones</p>
          </div>

          <div className="bg-gray-800 border border-gray-700 rounded-lg p-4">
            <p className="text-gray-400 text-xs font-semibold">Calificados</p>
            <p className="text-4xl font-bold text-cyan-400 mt-1">{stats.calificados}</p>
            <p className="text-xs text-gray-500 mt-2">Que califican</p>
          </div>

          <div className="bg-gray-800 border border-gray-700 rounded-lg p-4">
            <p className="text-gray-400 text-xs font-semibold">Tasa Cierre</p>
            <p className="text-4xl font-bold text-red-400 mt-1">{stats.tasa_cierre}%</p>
            <p className="text-xs text-gray-500 mt-2">De conversión</p>
          </div>
        </div>

        {/* CONTROLES */}
        <div className="bg-gray-800 border border-gray-700 rounded-lg p-4 mb-6">
          <div className="flex flex-col md:flex-row gap-4 items-center justify-between">
            <div className="flex-1 flex gap-4 w-full md:w-auto">
              <input
                type="text"
                placeholder="🔍 Buscar por nombre o DNI..."
                value={search}
                onChange={(e) => setSearch(e.target.value)}
                className="flex-1 px-4 py-2 bg-gray-700 border border-gray-600 rounded-lg text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-blue-500"
              />
            </div>

            <div className="flex gap-2 w-full md:w-auto">
              <select
                value={filterEtapa}
                onChange={(e) => setFilterEtapa(e.target.value)}
                className="px-4 py-2 bg-gray-700 border border-gray-600 rounded-lg text-white focus:outline-none focus:ring-2 focus:ring-blue-500"
              >
                <option value="todos">Todas las etapas</option>
                {ETAPAS.map((e) => (
                  <option key={e.id} value={e.id}>
                    {e.emoji} {e.label}
                  </option>
                ))}
              </select>

              <select
                value={sortBy}
                onChange={(e) => setSortBy(e.target.value)}
                className="px-4 py-2 bg-gray-700 border border-gray-600 rounded-lg text-white focus:outline-none focus:ring-2 focus:ring-blue-500"
              >
                <option value="fecha">📅 Más reciente</option>
                <option value="proximo-seguimiento">⏰ Próx. contacto</option>
                <option value="etapa">📊 Por etapa</option>
              </select>

              <button
                onClick={() => {
                  setEditingLead(null)
                  setFormData({
                    nombre: '',
                    dni: '',
                    tel: '',
                    email: '',
                    proyecto: 'Los Sauces',
                    lote_id: '',
                    ingresos: '',
                    tiene_propiedad: false,
                    etapa: 'nuevo',
                    fecha_seguimiento: new Date().toISOString().split('T')[0],
                    notas: '',
                  })
                  setShowForm(true)
                }}
                className="px-4 py-2 bg-blue-600 hover:bg-blue-700 rounded-lg font-semibold flex items-center gap-2 transition"
              >
                <Plus size={18} />
                Nuevo
              </button>
            </div>
          </div>
        </div>

        {/* TABLA */}
        <div className="bg-gray-800 border border-gray-700 rounded-lg overflow-hidden">
          <div className="overflow-x-auto">
            <table className="w-full text-sm">
              <thead className="bg-gray-700 border-b border-gray-600">
                <tr>
                  <th className="px-4 py-3 text-left font-semibold">Cliente</th>
                  <th className="px-4 py-3 text-left font-semibold">Proyecto</th>
                  <th className="px-4 py-3 text-left font-semibold">Etapa</th>
                  <th className="px-4 py-3 text-left font-semibold">Próx. Contacto</th>
                  <th className="px-4 py-3 text-center font-semibold">Califica</th>
                  <th className="px-4 py-3 text-center font-semibold">Acciones</th>
                </tr>
              </thead>
              <tbody>
                {leadsFiltrados.length === 0 ? (
                  <tr>
                    <td colSpan={6} className="px-4 py-8 text-center text-gray-400">
                      No hay leads. Crea uno para comenzar 👇
                    </td>
                  </tr>
                ) : (
                  leadsFiltrados.map((lead, i) => {
                    const etapa = ETAPAS.find((e) => e.id === lead.etapa)
                    const califica =
                      lead.ingresos && lead.ingresos <= 3626 && !lead.tiene_propiedad

                    const diasParaContacto = lead.fecha_seguimiento
                      ? Math.ceil(
                          (new Date(lead.fecha_seguimiento) - new Date()) /
                            (1000 * 60 * 60 * 24)
                        )
                      : null

                    return (
                      <tr
                        key={lead.id}
                        className={`border-b border-gray-700 hover:bg-gray-700 transition ${
                          i % 2 === 0 ? 'bg-gray-800' : 'bg-gray-750'
                        }`}
                      >
                        <td className="px-4 py-3 font-semibold text-white">
                          <div>{lead.nombre}</div>
                          <div className="text-xs text-gray-400 mt-1">{lead.dni}</div>
                        </td>
                        <td className="px-4 py-3 text-gray-300">{lead.proyecto}</td>
                        <td className="px-4 py-3">
                          <span
                            className={`px-2 py-1 rounded text-xs font-bold ${
                              etapa?.color || 'bg-gray-600 text-gray-300'
                            }`}
                          >
                            {etapa?.emoji} {etapa?.label}
                          </span>
                        </td>
                        <td className="px-4 py-3">
                          {diasParaContacto !== null ? (
                            <div className="text-xs">
                              <div
                                className={`font-semibold ${
                                  diasParaContacto <= 0
                                    ? 'text-red-400'
                                    : diasParaContacto <= 2
                                      ? 'text-yellow-400'
                                      : 'text-green-400'
                                }`}
                              >
                                {diasParaContacto <= 0 ? '⏰ HOY' : `${diasParaContacto}d`}
                              </div>
                              <div className="text-gray-500">
                                {new Date(lead.fecha_seguimiento).toLocaleDateString('es-PE')}
                              </div>
                            </div>
                          ) : (
                            <span className="text-gray-500 text-xs">-</span>
                          )}
                        </td>
                        <td className="px-4 py-3 text-center">
                          <span
                            className={`px-2 py-1 rounded text-xs font-bold ${
                              califica
                                ? 'bg-green-900 text-green-300'
                                : 'bg-red-900 text-red-300'
                            }`}
                          >
                            {califica ? '✅ SÍ' : '❌ NO'}
                          </span>
                        </td>
                        <td className="px-4 py-3">
                          <div className="flex gap-2 justify-center flex-wrap">
                            <button
                              onClick={() => generarCotizacion(lead)}
                              className="p-2 hover:bg-purple-900 rounded transition"
                              title="Cotizar"
                            >
                              <DollarSign size={16} className="text-purple-400" />
                            </button>
                            <button
                              onClick={() => enviarWhatsApp(lead)}
                              className="p-2 hover:bg-green-900 rounded transition"
                              title="WhatsApp"
                            >
                              <MessageCircle size={16} className="text-green-400" />
                            </button>
                            <button
                              onClick={() => {
                                setEditingLead(lead)
                                setFormData(lead)
                                setShowForm(true)
                              }}
                              className="p-2 hover:bg-blue-900 rounded transition"
                              title="Editar"
                            >
                              <Edit2 size={16} className="text-blue-400" />
                            </button>
                            <button
                              onClick={() => eliminarLead(lead.id)}
                              className="p-2 hover:bg-red-900 rounded transition"
                              title="Eliminar"
                            >
                              <Trash2 size={16} className="text-red-400" />
                            </button>
                          </div>
                        </td>
                      </tr>
                    )
                  })
                )}
              </tbody>
            </table>
          </div>
        </div>
      </main>

      {/* MODAL: NUEVO/EDITAR LEAD */}
      {showForm && (
        <div className="fixed inset-0 bg-black/70 flex items-center justify-center p-4 z-50 backdrop-blur-sm">
          <div className="bg-gray-800 border border-gray-700 rounded-lg p-6 w-full max-w-2xl max-h-[90vh] overflow-y-auto">
            <h2 className="text-2xl font-bold text-white mb-6">
              {editingLead ? '✏️ Editar Lead' : '➕ Nuevo Lead'}
            </h2>

            <div className="grid grid-cols-1 md:grid-cols-2 gap-4 mb-6">
              {/* DATOS PERSONALES */}
              <div>
                <label className="block text-sm font-semibold text-gray-300 mb-2">
                  Nombre *
                </label>
                <input
                  type="text"
                  placeholder="Nombre completo"
                  value={formData.nombre}
                  onChange={(e) => setFormData({ ...formData, nombre: e.target.value })}
                  className="w-full px-4 py-2 bg-gray-700 border border-gray-600 rounded-lg text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-blue-500"
                />
              </div>

              <div>
                <label className="block text-sm font-semibold text-gray-300 mb-2">
                  DNI *
                </label>
                <input
                  type="text"
                  placeholder="12345678"
                  value={formData.dni}
                  onChange={(e) => setFormData({ ...formData, dni: e.target.value })}
                  className="w-full px-4 py-2 bg-gray-700 border border-gray-600 rounded-lg text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-blue-500"
                />
              </div>

              <div>
                <label className="block text-sm font-semibold text-gray-300 mb-2">
                  WhatsApp
                </label>
                <input
                  type="tel"
                  placeholder="+51 999 888 777"
                  value={formData.tel}
                  onChange={(e) => setFormData({ ...formData, tel: e.target.value })}
                  className="w-full px-4 py-2 bg-gray-700 border border-gray-600 rounded-lg text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-blue-500"
                />
              </div>

              <div>
                <label className="block text-sm font-semibold text-gray-300 mb-2">
                  Email
                </label>
                <input
                  type="email"
                  placeholder="correo@ejemplo.com"
                  value={formData.email}
                  onChange={(e) => setFormData({ ...formData, email: e.target.value })}
                  className="w-full px-4 py-2 bg-gray-700 border border-gray-600 rounded-lg text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-blue-500"
                />
              </div>

              {/* DATOS INMOBILIARIOS */}
              <div>
                <label className="block text-sm font-semibold text-gray-300 mb-2">
                  Proyecto
                </label>
                <select
                  value={formData.proyecto}
                  onChange={(e) => setFormData({ ...formData, proyecto: e.target.value })}
                  className="w-full px-4 py-2 bg-gray-700 border border-gray-600 rounded-lg text-white focus:outline-none focus:ring-2 focus:ring-blue-500"
                >
                  {PROYECTOS.map((p) => (
                    <option key={p.nombre} value={p.nombre}>
                      {p.nombre}
                    </option>
                  ))}
                </select>
              </div>

              <div>
                <label className="block text-sm font-semibold text-gray-300 mb-2">
                  Lote
                </label>
                <select
                  value={formData.lote_id}
                  onChange={(e) => setFormData({ ...formData, lote_id: e.target.value })}
                  className="w-full px-4 py-2 bg-gray-700 border border-gray-600 rounded-lg text-white focus:outline-none focus:ring-2 focus:ring-blue-500"
                >
                  <option value="">Seleccionar lote</option>
                  {LOTES[formData.proyecto]?.map((l) => (
                    <option key={l.id} value={l.id}>
                      {l.id} - S/ {l.precio.toLocaleString()} ({l.area}m²)
                    </option>
                  ))}
                </select>
              </div>

              {/* DATOS FINANCIEROS */}
              <div>
                <label className="block text-sm font-semibold text-gray-300 mb-2">
                  Ingresos mensuales
                </label>
                <input
                  type="number"
                  placeholder="Ej: 2500"
                  value={formData.ingresos}
                  onChange={(e) => setFormData({ ...formData, ingresos: e.target.value })}
                  className="w-full px-4 py-2 bg-gray-700 border border-gray-600 rounded-lg text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-blue-500"
                />
              </div>

              {/* ESTADO */}
              <div>
                <label className="block text-sm font-semibold text-gray-300 mb-2">
                  Etapa
                </label>
                <select
                  value={formData.etapa}
                  onChange={(e) => setFormData({ ...formData, etapa: e.target.value })}
                  className="w-full px-4 py-2 bg-gray-700 border border-gray-600 rounded-lg text-white focus:outline-none focus:ring-2 focus:ring-blue-500"
                >
                  {ETAPAS.map((e) => (
                    <option key={e.id} value={e.id}>
                      {e.emoji} {e.label}
                    </option>
                  ))}
                </select>
              </div>

              <div>
                <label className="block text-sm font-semibold text-gray-300 mb-2">
                  Próx. seguimiento
                </label>
                <input
                  type="date"
                  value={formData.fecha_seguimiento}
                  onChange={(e) =>
                    setFormData({ ...formData, fecha_seguimiento: e.target.value })
                  }
                  className="w-full px-4 py-2 bg-gray-700 border border-gray-600 rounded-lg text-white focus:outline-none focus:ring-2 focus:ring-blue-500"
                />
              </div>
            </div>

            {/* CHECKBOX */}
            <div className="mb-6">
              <label className="flex items-center gap-3 cursor-pointer">
                <input
                  type="checkbox"
                  checked={formData.tiene_propiedad}
                  onChange={(e) => setFormData({ ...formData, tiene_propiedad: e.target.checked })}
                  className="w-4 h-4 rounded accent-blue-500"
                />
                <span className="text-white font-semibold">
                  ¿Tiene propiedad registrada en SUNARP?
                </span>
              </label>
            </div>

            {/* NOTAS */}
            <div className="mb-6">
              <label className="block text-sm font-semibold text-gray-300 mb-2">
                Notas
              </label>
              <textarea
                placeholder="Observaciones, objeciones, llamadas..."
                value={formData.notas}
                onChange={(e) => setFormData({ ...formData, notas: e.target.value })}
                rows={3}
                className="w-full px-4 py-2 bg-gray-700 border border-gray-600 rounded-lg text-white placeholder-gray-400 focus:outline-none focus:ring-2 focus:ring-blue-500"
              />
            </div>

            {/* BOTONES */}
            <div className="flex gap-4">
              <button
                onClick={() => setShowForm(false)}
                className="flex-1 px-4 py-2 bg-gray-700 hover:bg-gray-600 rounded-lg text-white font-semibold transition"
              >
                Cancelar
              </button>
              <button
                onClick={guardarLead}
                disabled={loading}
                className="flex-1 px-4 py-2 bg-blue-600 hover:bg-blue-700 rounded-lg text-white font-semibold disabled:opacity-50 transition"
              >
                {loading ? 'Guardando...' : 'Guardar'}
              </button>
            </div>
          </div>
        </div>
      )}

      {/* MODAL: COTIZACIÓN */}
      {cotizacion && (
        <div className="fixed inset-0 bg-black/70 flex items-center justify-center p-4 z-50 backdrop-blur-sm">
          <div className="bg-gray-800 border border-gray-700 rounded-lg w-full max-w-2xl max-h-[90vh] overflow-y-auto">
            {/* HEADER */}
            <div className="bg-gradient-to-r from-blue-600 to-purple-600 p-6 flex justify-between items-center">
              <h2 className="text-3xl font-bold text-white">💰 Cotización</h2>
              <button
                onClick={() => setCotizacion(null)}
                className="text-white hover:bg-white/20 p-2 rounded-lg transition"
              >
                ✕
              </button>
            </div>

            <div className="p-6 space-y-6">
              {/* CLIENTE */}
              <div className="bg-gray-700 border border-gray-600 rounded-lg p-4">
                <h3 className="font-bold text-white mb-2">👤 Cliente</h3>
                <p className="text-white text-sm">
                  <strong>{cotizacion.lead.nombre}</strong> - DNI: {cotizacion.lead.dni}
                </p>
                <p className="text-gray-400 text-sm">{cotizacion.lead.tel}</p>
              </div>

              {/* DESGLOSE FINANCIERO */}
              <div className="bg-blue-900 border border-blue-700 rounded-lg p-4">
                <h3 className="font-bold text-white mb-4">📊 Desglose Financiero</h3>
                <div className="space-y-3 text-sm">
                  <div className="flex justify-between">
                    <span className="text-gray-300">Proyecto:</span>
                    <span className="font-bold text-white">{cotizacion.data.proyecto}</span>
                  </div>
                  <div className="flex justify-between">
                    <span className="text-gray-300">Lote:</span>
                    <span className="font-bold text-white">{cotizacion.data.loteId}</span>
                  </div>
                  <div className="flex justify-between">
                    <span className="text-gray-300">Tipo:</span>
                    <span className="text-white">{cotizacion.data.tipo}</span>
                  </div>
                  <div className="flex justify-between">
                    <span className="text-gray-300">Área:</span>
                    <span className="text-white">{cotizacion.data.area}m²</span>
                  </div>

                  <div className="border-t border-blue-700 pt-3 mt-3">
                    <div className="flex justify-between">
                      <span className="text-gray-300">Precio:</span>
                      <span className="font-bold text-white">
                        S/ {cotizacion.data.precio.toLocaleString()}
                      </span>
                    </div>
                    <div className="flex justify-between text-green-300">
                      <span>(-) Bono TP:</span>
                      <span className="font-bold">
                        S/ {cotizacion.data.bono.toLocaleString()}
                      </span>
                    </div>
                    <div className="flex justify-between text-green-300">
                      <span>(-) Descuento:</span>
                      <span className="font-bold">
                        S/ {cotizacion.data.descTotal.toLocaleString()}
                      </span>
                    </div>
                    <div className="flex justify-between text-green-300">
                      <span>(-) Inicial:</span>
                      <span className="font-bold">
                        S/ {cotizacion.data.inicialCliente.toLocaleString()}
                      </span>
                    </div>

                    <div className="border-t border-blue-700 pt-3 mt-3 flex justify-between">
                      <span className="text-gray-300">Saldo a financiar:</span>
                      <span className="font-bold text-white">
                        S/ {cotizacion.data.saldoFinanciar.toLocaleString()}
                      </span>
                    </div>
                  </div>
                </div>
              </div>

              {/* CUOTA MENSUAL */}
              <div className="bg-green-900 border border-green-700 rounded-lg p-6 text-center">
                <p className="text-gray-300 text-sm mb-2">📈 Cuota Mensual (42 meses)</p>
                <p className="text-5xl font-bold text-green-300">
                  S/ {cotizacion.data.cuotaRegular.toFixed(2)}
                </p>
                <p className="text-xs text-gray-400 mt-3">Sin intereses · Plazo fijo</p>
              </div>

              {/* ANÁLISIS IA */}
              <div className="bg-purple-900 border border-purple-700 rounded-lg p-4">
                <h3 className="font-bold text-white mb-3">🤖 Análisis de Venta (IA)</h3>
                <p className="text-gray-300 text-sm whitespace-pre-wrap leading-relaxed">
                  {cotizacion.analisis}
                </p>
              </div>

              {/* BOTONES */}
              <div className="flex gap-4">
                <button
                  onClick={() => setCotizacion(null)}
                  className="flex-1 px-4 py-3 bg-gray-700 hover:bg-gray-600 rounded-lg text-white font-semibold transition"
                >
                  Cerrar
                </button>
                <button
                  onClick={enviarCotizacionWhatsApp}
                  className="flex-1 px-4 py-3 bg-green-600 hover:bg-green-700 rounded-lg text-white font-semibold flex items-center justify-center gap-2 transition"
                >
                  <MessageCircle size={18} />
                  📱 Enviar por WhatsApp
                </button>
              </div>
            </div>
          </div>
        </div>
      )}
    </div>
  )
}
