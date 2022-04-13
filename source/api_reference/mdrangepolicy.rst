
.. _mdrandepolicy:

``Kokkos::MDRangePolicy``
=========================

Header File: ``Kokkos_Core.hpp``

Class Interface
---------------

.. cpp:class:: template<class ... Args> Kokkos::MDRangePolicy

  `MDRangePolicy` defines an execution policy for a multi dimensional iteration space starting at a `begin` tuple and going to `end` with an open interval. The iteration space will be tiled, and the user can optionally provide tiling sizes.

  .. cpp:function:: MDRangePolicy()

      Default constructor uninitialized policy.

  .. cpp:function:: MDRangePolicy(const Kokkos::Array<int64_t,rank>& begin, \
                                  const Kokkos::Array<int64_t,rank>& end)

      Constructor accepting a start and end index.

  .. cpp:function:: MDRangePolicy(const Kokkos::Array<int64_t,rank>& begin, \
                                  const Kokkos::Array<int64_t,rank>& end, \
                                  const Kokkos::Array<int64_t,rank>& tiling)

      Constructor accepting a start, end index and the tiling dimensions.


  .. cpp:function:: template<class OT, class IT, class TT> MDRangePolicy(const std::initializer_list<OT>& begin, const std::initializer_list<IT>& end)

      Provide a start and end index. The length of the lists must match the rank of the policy.


  .. cpp:function::  template<class OT, class IT, class TT> MDRangePolicy(const std::initializer_list<OT>& begin, const std::initializer_list<IT>& end,  std::initializer_list<TT>& tiling)

      Provide a start and end index as well as the tiling dimensions. The length of the lists must match the rank of the policy.


Usage:
------

.. code-block:: cpp

  Kokkos::MDRangePolicy<>(begin, end)
  Kokkos::MDRangePolicy<>(Space, begin, end)
  Kokkos::MDRangePolicy<ARGS>(begin, end, tiling)
  Kokkos::MDRangePolicy<ARGS>(Space, begin, end, tiling)



Parameters:
-----------

* All `common arguments listed here <executionpolicies>`__ can be used for this policy

* ``MDRangePolicy`` specifically accepts:

.. code-block:: cpp

  template<int N, Iterate outer, Iterate inner>
  class Rank;

Which determines the rank of the index space as well as in which order to iterate over the tiles and how to iterate within the tiles. ``outer`` and ``inner`` can be ``Kokkos::Iterate::Default``, ``Kokkos::Iterate::Left``, or ``Kokkos::Iterate::Right``.



Examples
--------

.. code-block:: cpp

  MDRangePolicy<Rank<3>> policy_1({0,0,0},{N0,N1,N2});
  MDRangePolicy<Cuda,Rank<3,Iterate::Right,Iterate::Left>> policy_2({5,5,5},{N0-5,N1-5,N2-5},{T0,T1,T2});
